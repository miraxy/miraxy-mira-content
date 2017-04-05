---
utid: 20190
date: 2017-03-28 19:14:35
title: post template
_index: 
chapter: 07
chaptername: گام ششم: ساختن قالب
---
فایل post.tt2 برای ساختن قالب تکی پست‌ها و نوشته در آدرسی است که در فیلد permalink در تنظیمات سایت مشخص کرده‌ایم استفاده می‌شود.

در این مثال، آدرس‌های زیر با استفاده از این قالب ساخته می‌شوند:

	address.com/blog/category/year/month/day/post_title.html
	address.com/en/year/month/day/post_title/
	address.com/linux/author/post_title/
	address.com/story/category/post_title/

اگر به قالب‌های index و archive یک بار دیگر نگاه بیندازید میبینید که پست ها را با استفاده از یک حلقه {{ FOREACH post IN POSTS }} لود کردیم، در مورد post اما استفاده از این حلقه اجباری نیست، یعنی اگر از آن استفاده نکنیم باز هم **post** مقدار معتبری دارد.

هر دو کد زیر برای استفاده در post معتبر هستند:
	<td>
	{{ Foreach post IN POSTS }}
		{{ post.title }}
	{{ END }}
	</td>

	<td>
		{{ post.title }}
	</td>

در post.tt2 استفاده از حلقه POSTS زمانی مفید است که بخواهید با متغیر دیگری به جز post مقادیر را فراخوانی کنید، مثلا:

	<td>
	{{ Foreach entry IN POSTS }}
		{{ entry.title }}
	{{ END }}
	</td>

به جز این مورد تقریبا تمام برچسب‌های دیگر بین archive، post و index شبیه به هم هستند و معتبر. پس میتوانیم عینا از قالب index برای post هم استفاده کنیم، اما عملا این کار برای قالبی که در حال ساخت آن هستیم مفید نیست، چرا که در قالب index خلاصه نوشته ها را برای نمایش در نظر گرفتیم و نه متن کامل یا در index و archive جزییات زیادی از هر پست را لود نکردیم، مثلا در سایت آموزش لینوکس هر نوشته نام نویسنده‌ی متفاوتی داشت، یا دسته بندی‌هایی که انجام داد بودیم، مثل tag ها در وبلاگ ها یا keywordها در داستان و عکس اختصاصی که برای نوشته‌های وبلاگ فارسی و آموزش لینوکس داشتیم و category ها. البته تمام این موارد را میشود در قالب‌های index یا archive هم نمایش داد، اما برای ساده بودن قالب از آن‌ها چشم پوشی شده.

اما نحوه‌ی اضافه کردن، تمام مشخصات هر نوشته که در هدر به آن نسبت داده شده مثل تاریخ، category، tag و ... در حلقه POSTS قابل بازیابی است، مثلا {{ post.category }}، البته برای لود کردن مقادیر گروهی یا آرشیوها باید از یک حلقه‌ها جدید داخل حلقه قبلی استفاده کنیم:

	{{ FOREACH kw IN post.keywords }}
		{{ kw }}
	{{ END }}

و اگر مقداری که فراخوانی میکنیم را قبلا آرشیو کرده باشیم، یعنی مقدارش را در فایل تنظیمات به فیلد lists وارد کرده باشیم:

	{{ FOREACH tag IN post.tags.values }}
		<a href="{{ tag.url }}">{{ tag.name }}</a>
	{{ END }}

از آنجا که برای تمام سایت‌ها میخواهیم از یک قالب استفاده کنیم و لیست‌های آرشیو و فیلدهای سربرگ که برای هرکدام در نظر گرفتیم با دیگران متفاوت است، از عبارت شرطی {{ IF }} برای تست اینکه آیا فیلد مورد نظر در این پست وجود دارد یا نه کمک میگیریم، مثلا پست‌های وبلاگ داستان فیلد tags را در سربرگ نداشتند.

	{{ IF tags }}
	{{ FOREACH tag IN post.tags.values }}
		<a href="{{ tag.url }}">{{ tag.name }}</a>
	{{ END }}
	{{ END }}

یک بار دیگر به جزییات سربرگ‌هایی که داشتیم برگردیم، تمام فیلدهایی که برای هر چهار سایت در نظر گرفته بودیم، این فیلدها بودند:

	image
	description
	author
	category
	tags
	categories
	keywords
	suggests

که به جز keywords و suggests، در story و image در آموزش لینوکس و وبلاگ فارسی، مابقی را به عنوان لیست آرشیو برای سایت‌هایشان هم در نظر گرفته بودیم. با توجه به تمام توضیحاتی که دادیم قالب post را به این صورت می‌سازیم، کدهای زیر را در post.tt2 کپی کنید:

	<!DOCTYPE html>
	<html xmlns="http://www.w3.org/1999/xhtml" lang="en" xml:lang="en">
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
	    </style>
	</head>
	<body>
	<body>
		<center>
		<img src="{{ SITE.author_image }}">
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
		  {{ IF post.description }}description: {{ post.description }}{{ END }}<br>
		  {{ IF post.image }}<img src="{{ post.image }}">{{ END }}
		  {{ IF post.author }}
		  author: {{ FOREACH author IN post.author.values }}<a href="{{ author.url }}">{{ author.name }}</a>{{ END }}<br>
		  {{ END }}
		  <p>{{ post.body.more }}</p>
		  {{ IF post.category }}
		  category: {{ FOREACH cat IN post.category.values }}<a href="{{ cat.url }}">{{ cat.name }}</a>{{ END }}<br>
		  {{ END }}
		  {{ IF post.tags }}
		  tags: {{ FOREACH tag IN post.tags.values }}<a href="{{ tag.url }}">{{ tag.name }}</a>/{{ END }}<br>
		  {{ END }}
		  {{ IF post.categories }}
		  categories: {{ FOREACH cat IN post.categories.values }}<a href="{{ cat.url }}">{{ cat.name }}</a>/{{ END }}<br>
		  {{ END }}
		  {{ IF post.keywords }}
		  keywords: {{ FOREACH kw IN post.keywords }}{{ kw }}/{{ END }}<br>
		  {{ END }}
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
	  	    <a href="{{ PAGE.prev.url }}">prev: {{ PAGE.prev.title }}</a>
		  {{- END }}
			|
		  {{ IF PAGE.next }}
	      	    <a href="{{ PAGE.next.url }}">next: {{ PAGE.next.title }}</a>
		  {{- END }}
		  </td>
		</tr>	
		</table>
	</body>
	</html>

**نکته**:  
پیش از این در قسمت تنظیمات گفته شد که هر فیلدی که در تنظیمات اختصاصی سایت نباشد، مقدارش برابر با مقداری است که در فایل تنظیمات عمومی وجود دارد، اگر به یاد داشته باشید برای همین هم در تنظیم سایت دنباله دار، فیلد لیست را به صورت خالی وارد کردیم.

حالا خطوط ۷ و ۱۷ قالب post را ببینید، در تنظیمات هیچ‌کدام از سایت‌ها فیلدی به نام author_image وجود نداشت این فیلد را تنها در تنظیمات عمومی نوشته بودیم، اما در خط ۱۷ به جای MAIN که متعلق به تنظیمات عمومی است، با SITE که برای تنظیمات سایت‌هاست، آن را لود کرده‌ایم و مقدار معتبری بر میگرداند.  
البته استفاده از این تگ منطقی نیست و فقط برای مثال و درک بهتر کارکرد فیلدها در تنظیمات به این صورت نوشته شده.
