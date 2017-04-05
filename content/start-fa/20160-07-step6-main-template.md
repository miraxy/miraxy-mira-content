---
utid: 20160
date: 2017-03-28 19:06:14
title: main template
_index: 
chapter: 07
chaptername: گام ششم: ساختن قالب
---
فایل main.tt2 برای ساختن یک قالب مشترک بین تمام سایت‌هاست، یک صفحه ارتباطی.

مسیری که به عنوان url و root در فایل config.yml مشخص کرده باشید با استفاده از این قالب ساخته می‌شود.

در این مثال این صفحه با استفاده از این قالب ساخته می‌شود.

	address.com/index.html

این فایل را با هر ویرایشگری که دوست دارید باز کنید و کدهای زیر را در آن کپی کنید

	<!DOCTYPE html>
	<html xmlns="http://www.w3.org/1999/xhtml" lang="en" xml:lang="en">
	<head>
	    <meta charset="utf-8">
	    <meta name="description" content="{{ MainDESCRIPTION }}">
	    <meta name="author" content="{{ MainAUTHOR }}">
	    <link rel="shortcut icon" href="{{ MAIN.author_image }}">
	    <title>{{ PageTITLE }}</title>
	    <style>
	    entry img {
		max-width: 100% !important;
	    }
	    </style>
	</head>
	<body>
		<center>
		<img src="{{ MAIN.logo }}">
		<h1>{{ MainTITLE }}</h1>
		<h2>{{ MainDESCRIPTION }}</h2>
		</center>
		<hr>
		<table>
		<tr>
		{{ FOREACH site IN FLOORS.values.sort('name') }}
		  <td style="border-right: 1px solid black; width: 25%;" valign="top">
		  <h2><a href="{{ site.root }}">{{ site.name }}</a></h2>
		  <p>{{ site.description }}</p>
		  <hr>
		  <ul>
		  {{ FOREACH post IN site.posts }}
			<li><h4><a href="{{ post.url }}">{{ post.title }}</a><h4></li>
			{{ post.body.less }}
		  {{ END }}
		  </ul>
		  </td>
		{{ END }}
		</tr>
		</table>

	</body>
	</html>

**نکته**: تمام مواردی را که در تنظیمات ذخیره شده می‌توان با استفاده از بر چسب‌های MAIN و SITE در قالب نیز فراخوانی کرد، مانند خط ۲۱ همین قالب که با استفاده از {{ MAIN.logo }} مقداری را که در config.yml ذخیره کرده بودیم را فراخوانی کردیم.

همیچنین می‌توان تنظیماتی که در شاخه‌ی config و برای هر سایت مشخص کرده‌ایم را به این شکل فراخوانی کرد: {{ SITE.lang }} و ...

حالا که یک قالب داریم میتوانیم اولین build را انجام دهیم:

	mira build

یک نسخه‌ی قابل انتشار از سایت در شاخه‌ی public به وجود آمده، حالا با دستور 
	mira view

یک سرور برای پیش نمایش اجرا می‌کینم.

حالا به این آدرس بروید:

[127.0.0.1:5000](//127.0.0.1:5000)
