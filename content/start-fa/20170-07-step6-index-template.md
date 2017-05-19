---
utid: 20170
date: 2017-03-28 19:09:26
title: index template
_index: 
chapter: 07
chaptername: گام ششم: ساختن قالب
---
فایل index.tt2 برای ساختن صفحه‌ی اصلی هر سایت در آدرسی است که برای آن در فیلدهای url و root تنظیماتش مشخص کرده‌اید.

در این مثال، آدرس‌های زیر با استفاده از این قالب ساخته می‌شوند:

	address.com/blog/
	address.com/blog/page/1/ , address.com/blog/page/2/ ...

	address.com/en/
	address.com/en/page/1/ , address.com/en/page/1/ ...

	address.com/story/ ...
	address.com/linux/ ...

کدهای زیر را در index.tt2 کپی کنید:

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
		<center>
		<img src="{{ MAIN.logo }}">
		<h1>{{ TITLE }}</h1>
		<h2>{{ DESCRIPTION }}</h2>
		</center>
		<hr>
		<table>
		<tr>
	<!-- Content -->
		<td width="70%">
		{{ FOREACH post IN POSTS }}
		  <h2><a href="{{ post.url }}">{{ post.title }}</a></h2>
		  <h5>{{ post.CALENDAR.jday_name }} {{ post.CALENDAR.jday }} {{ post.CALENDAR.jmonth_name }} {{ post.CALENDAR.jyear }}</h5>
		  <h5>{{ post.CALENDAR.day_name }} {{ post.CALENDAR.day }} {{ post.CALENDAR.month_name }} {{ post.CALENDAR.year }}</h5>
		  <p>{{ post.body.less }}</p>
		  <br>
		  <a href="{{ url }}#more">Continue...</a>
		  <hr>
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

از آنجا که بدنه اصلی کدهای تشکیل دهنده‌ی index، archive و post تقریبا یکی است، در مورد این کدها بعد از ساختن قالب post بیشتر توضیح می‌دهیم. و توضیحات تکمیلی‌تر را هم بعد از ساختن atom.tt2 با هم مرور می‌کینم.
