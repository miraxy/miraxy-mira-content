---
utid: 20180
date: 2017-03-28 19:12:38
title: archive template
_index: 
chapter: 07
chaptername: گام ششم: ساختن قالب
---
فایل archive.tt2 حاوی قالب ساخت تمام صفحات آرشیو است، برای مثال این صفحه‌ها:

	/blog/category/anime/
	/blog/archive/1395/08/
	/en/tags/Promise/

فایل archive.tt2 را برای ویرایش باز کنید و کدهای زیر را در آن کپی کنید:

	<!DOCTYPE html>
	<html xmlns="http://www.w3.org/1999/xhtml" lang="en" xml:lang="en">
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
	    </style>
	</head>
	<body>
	<body>
		<center>
		<img src="{{ MAIN.logo }}">
		<h1>{{ TITLE }}</h1>
		<h2>{{ ArchiveTITLE }}</h2>
		</center>
		<hr>
		<table>
		<tr>
	<!-- Content -->
		<td width="70%">
		{{ FOREACH post IN POSTS }}
		  <h2><a href="{{ post.url }}">{{ post.title }}</a></h2>
		{{ END }}
		</td>
	<!-- sidebar -->
		<td width="30%">
		</td>
		</tr>
	<!-- pagination -->
		<tr>
		  <td width="30%">
		  {{ IF PAGE.prev }}
  		    <a href="{{ PAGE.prev.url }}">prev: page {{ PAGE.prev.title }}</a>
		  {{- END }}
		    | page {{ PAGE.number }} of {{PAGE.total}} |
		  {{ IF PAGE.next }}
      		    <a href="{{ PAGE.next.url }}">next: page {{ PAGE.next.title }}</a>
		  {{- END }}
		  </td>
		</tr>	
		</table>
	</body>
	</html>

اگر به قالب‌های index و archive دقت کنید، تقریبا شبیه به هم هستند و تفاوت‌ها جزیی است، البته در index خلاصه متن را با {{ post.body.less }} فراخوانی کردیم، یا تاریخ‌ها را با برچسب‌های {{ post.CALENDAR }}، اما در قالب archive ما این برچسب‌ها نیستند، که به صورت اختیاری حذف شده‌اند و اگر نیازی داشته باشید می‌توانید از تمامشان استفاده کنید، تنها تفاوت بین این دو قالب {{ ArchiveTITLE }} است که در index یک برچسب نامعتبر به حساب می‌آید.
