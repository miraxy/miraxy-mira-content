---
utid: 20220
date: 2017-03-28 19:34:44
title: تکمیل کردن قالب post
_index: post subjoin
chapter: 07
chaptername: گام ششم: ساختن قالب
---
زمانی که داشتیم سربرگ‌ها را تنظیم می‌کردیم برای سایت داستان ها یا همان دنباله دار، یک فیلد به نام suggests برای نمایش دادن داستان‌های مشابه تعریف کردیم که تا اینجا از آن استفاده نکردیم، حالا وقت آن رسیده که این فلد را هم به قالبمان اضافه کنیم.

در فایلی که برای محتوا دانلود کردید، به این شاخه‌ی story بروید و این دو فایل را باز کنید:

	~/mira/content/story/1394-12-11-the-selfish-gene.md
	~/mira/content/story/1395-2-27-sleep.md

در فایل sleep در فیلد suggests آدرس ایستای دو داستان دیگر وارد شده، برای نمایش دادن آن می‌توان از کدی شبیه به این استفاده کرد:

	{{ FOREACH suggest IN post.suggests }}
		{{ FOREACH entry IN ENTRIES.values }}
			{{ IF entry.url == suggest }}
				<a href="{{ entry.url }}">{{ entry.title }}</a><br>
			{{ END }}
		{{ END }}
	{{ END }}

در یک حلقه مقدار هر آدرس را در suggest لود کردیم، سپس در حلقه‌ی درونی تمام پست‌ها را گشتیم، اگر پستی که آدرس مشابه با suggest داست، نام و آدرس آن را نمایش دادیم.

در فایل the-selfish-gene اما utid دو داستان را برای suggests وارد کردیم، برای نمایش دادنشان از کدهای زیر می‌توان استفاده کرد:

	{{ FOREACH suggest IN post.suggests }}
		{{ IF ENTRIES.$suggest.url }}
			<a href="{{ ENTRIES.$suggest.url }}">{{ ENTRIES.$suggest.title }}</a><br>
		{{ END }}
	{{ END }}

باز هم در یک حلقه suggets های هر پست را می‌خوانیم، اما اینبار نیازی به حلقه‌ی درونی نیست، فقط تست میکنیم آیا پستی با این utid وجود دارد یا نه، اگر وجود داشت، نام و آدرس آن را نمایش می‌دهیم.

برای اینکه از هر دو روش همزمان در قالب استفاده کنیم، یک بار دیگر فایل post.tt2 را برای ویرایش کردن باز کنید، این چند خط را پیدا کنید:

	{{ IF post.keywords }}
	keywords: {{ FOREACH kw IN post.keywords }}{{ kw }}/{{ END }}<br>
	{{ END }}
کد زیر را بعد از آن اضافه کنید:

	{{ IF post.suggests }}
		<hr/>
	<p>suggests:</p>
	{{ FOREACH suggest IN post.suggests }}
		{{ IF ENTRIES.$suggest.url }}
			<a href="{{ ENTRIES.$suggest.url }}">{{ ENTRIES.$suggest.title }}</a><br>
		{{ END }}
		{{ FOREACH entry IN ENTRIES.values }}
		{{ IF entry.url == suggest }}
				<a href="{{ entry.url }}">{{ entry.title }}</a><br>
			{{ END }}
		{{ END }}
	{{ END }}
	{{ END }}
