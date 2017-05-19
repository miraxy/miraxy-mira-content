---
utid: 20250
date: 2017-03-28 19:50:13
title: ساختن صفحات
_index: pages
chapter: 08
chaptername: گام هفتم: شخصی سازی بیشتر
---
برای ساختن صفحات ثابت جدا از روند اصلی سایت، مثل صفحه درباره یا تماس و ... با اضافه کردن فیلد type و مقدار page در هدر هر پست، آن پست را به عنوان صفحه ثابت به میرا معرفی می‌کنیم، این کار باعث میشود که پست مورد نظر از لیست‌های مطالب برای نمایش در صفحه اول یا سایر صفحه‌های سایت و page.next و page.prev برای حرکت بین پست‌ها حذف شده و تنها با وارد کردن آدرس مستقیم آن نمایش داده شود.

در وبلاگ فارسی یک پست جدید بسازید:

	mira new -t 'about me' -f blog-fa

حالا آن را ویرایش کنید:

	---
	utid: 20170328195013
	title: درباره من
	_index: about
	_type: page
	_layout: page
	_permalink: /:title/
	---
	این صفحه در باره من است، اینجا مقداری در مورد خودم توضیح می‌دهم

حالا در شاخه‌ی قالب my-theme یک فایل جدید به نام page بسازید:

	~/mira/template/my-theme/page

و مقادیر زیر را در آن کپی کنید:

	<!DOCTYPE html>
	<html>
	<head>
	    <meta charset="utf-8">
	    <meta name="description" content="{{ DESCRIPTION }}">
	    <meta name="author" content="{{ MainAUTHOR }}">
	    <link rel="shortcut icon" href="{{ MAIN.author_image }}">
	    <title>{{ PageTITLE }}</title>
	    <style>
	    img {
		max-width: 100% !important;
	    }
		{{ IF SITE.lang == 'fa' }}
		body {
		   direction: rtl;
		}
		{{ END }}
		{{ IF SITE.lang == 'en' }}
		body {
		   direction: ltr;
		}
		{{ END }}
	    </style>
	</head>
	<body>
		<center>
		<img src="{{ SITE.author_image }}">
		<h1>{{ post.title }}</h1>
		</center>
		<hr>
		<table>
		<tr>
		<td>
		  <p>{{ post.body.more }}</p>
		</td>
		</tr>
		</table>
	</body>
	</html>

این پست در صفحه اصلی یا هیچ‌کجای دیگر سایت نمایش داده نخواهد شد، تنها راه دسترسی به آن دادن لینک مستقیم به این صفحه در این آدرس است:

	/blog/about/
