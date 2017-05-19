---
utid: 20230
date: 2017-03-28 20:08:44
title: مرتب کردن چیدمان
_index: layout
chapter: 07
chaptername: گام ششم: ساختن قالب
---
اگر تا این مرحله دستور build را اجرا نکردید، حتما یک بار آن را امتحان کنید

	mira build

و بعد یک پیش نمایش از سایت را برای خود اجرا کنید:

	mira view

حالا به این آدرس بروید:

[127.0.0.1:5000/blog/](//127.0.0.1:5000/blog/)

می‌بینید که همه نوشته‌ها چپ به راست نوشته شده‌اند و اصلا برای نمایش زبان فارسی مناسب نیستند.

همانطور که در تنظیم پیکربندی دیدید، در تنظیم هر سایت یک فیلد به نام lang را ساخته بودیم، حالا زمان استفاده از آن است.

برای راست‌چین کردن محتوای فارسی از یک شرط IF و مقدار فیلد lang در فایل config اختصاصی هر سایت استفاده میکنیم.

استفاده از مقدار فایل‌های config اختصاصی طبقات در قالب main و سایر قالب‌ها با هم متفاوت است. برای اینکه از این مقادیر در main استفاده کنیم، حتما باید داخل حلقه‌ی FLOORS باشیم، اما در سایر قالب‌ها در هر جای قالب که باشیم قابل دسترسی هستند.

برای اینکه تنوع استفاده و روش‌های متفاوت استفاده از بلوک‌های شرطی IF را ببینید، با دو روش متفاوت این مثال را پیش می‌بریم. انتخاب روش دلخواه با خود شماست.

یک بار دیگر فایل main.tt2 را باز کنید و به حلقه‌ی FOREACH FLOORS این کدها را اضافه کنید:

	{{ IF site.SITE.lang == 'fa' }}
	   <div dir="rtl">
	{{ ELSE }}
	   <div>
	{{ END }}

حالا باید نتیجه چیزی شبیه به این شده باشد:

	{{ FOREACH site IN FLOORS.values.sort('name') }}
	  <td style="border-right: 1px solid black; width: 25%;" valign="top">
	     {{ IF site.SITE.lang == 'fa' }}   <!-- add -->
		<div dir="rtl">                <!-- add -->
	     {{ ELSE }}                        <!-- add -->
		<div>                          <!-- add -->
	     {{ END }}                         <!-- add -->
	  <h2><a href="{{ site.root }}">{{ site.name }}</a></h2>
	  <p>{{ site.description }}</p>
	  <hr>
	  <ul>
	  {{ FOREACH post IN site.posts }}
		<li><h4><a href="{{ post.url }}">{{ post.title }}</a><h4></li>
		{{ post.body.less }}
	  {{ END }}
	  </ul>
	     </div>                            <!-- add -->
	  </td>
	{{ END }} 

حالا فایل‌های post.tt2، archive.tt2 و index.tt2 را باز کنید و این شرط را در قسمت head سایت به style اضافه کنید:

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

حالا head باید به این شکل در آمده باشد:

	<head>
	    <meta charset="utf-8">
	    <meta name="description" content="{{ DESCRIPTION }}">
	    <meta name="author" content="{{ MainAUTHOR }}">
	    <link rel="shortcut icon" href="{{ MAIN.author_image }}">
	    <title>{{ PageTITLE }}</title>
	    <style>
	    entry img {
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

**نکته**: برای استفاده از IF به جز ELSE از ELSIF هم می‌توانید استفاده کنید.
