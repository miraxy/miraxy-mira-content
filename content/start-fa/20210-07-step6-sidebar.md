---
utid: 20210
date: 2017-03-28 19:28:03
title: ساختن یک ساید بار
_index: sidebar
chapter: 07
chaptername: گام ششم: ساختن قالب
---
حالا وقت آن رسیده که با ساختن یک ساید بار آرشیوهایی که برای هر سایت را داشتیم را هم به نمایش درآوریم، برای این کار قبلا در میانه‌های قالب‌های index، archive و post یک قسمت را آماده گذشاته بودیم:

	<!-- sidebar -->
	<td width="30%">
	</td>

حالا زمان آن را رسیده که آن را تکمیل کنیم. برای نمایش لیست‌های آرشیو دو راه حل داریم، یکی به شکل کلی تمام آرشیوهای موجود را لود کنیم، مانند کاری که در انتهای قالب atom کرده بودیم، و یکی هم مثل قالب post، روشی که به ما امکان میدهد هر لیست را جدا و در جایی که میخواهیم نمایش دهیم.

#### روش اول، لود کردن همه چیز:

	{{ FOREACH archive IN ARCHIVES.pairs }}
	  <h5>{{ archive.key }}</h5><!-- archive name, like tags or dates ... -->
	  <hr>
	  {{ FOREACH item IN archive.value.values.sort('name').sort('number') }}
	    <a href="{{ item.url }}">{{ item.name }}</a>
	    {{ IF (archive.key == 'categories') }}<br>{{ END }}
	    {{ IF (archive.key == 'date') or (archive.key == 'jdate') }}<br>{{ END }}
	    {{ IF (archive.key == 'author') }}<br>{{ END }}
	    {{ IF (loop.index != loop.max) and (archive.key == 'tags') }}&nbsp;-&nbsp;{{ END }}
	    {{ IF (archive.key == 'category') }}
		<br>
		{{ FOREACH utid IN item.posts }}
			&nbsp;&nbsp;-&nbsp;<a href="{{ ENTRIES.$utid.url }}">{{ ENTRIES.$utid.title }}</a><br>
		{{ END }}
	    {{ END }}
	  {{- END }}
	  <br>
	{{- END }}

**توضیح:**

ابتدا یک جفت کلید-مقدار از آرشیوها را در متغیری به نام archive لود کردیم archive IN ARCHIVES.pairs، کلید با نام key حاوی نام آرشیو است، مثل category یا tag یا هر چیز دیگری {{ archive.key }}.

مقدار یا value حاوی یک لیست از اطلاعات مربوط به آن آرشیو است archive.value، که این لیست شامل این اطلاعات است: نام، آدرس لینک هر آرشیو، و utid پست‌هایی که در این آرشیو هستند. مثل همیشه، برای نمایش دادن لیست‌ها از FOREACH استفاده می‌کینم.

	{{ FOREACH item IN archive.value.values.sort('name').sort('number') }}

و البته با استفاده از sort، ترتیب نمایش را هم مشخص کردیم که بر اساس نام باشد و اگر نام‌های مشابه پیدا کرد، اولویت با تعداد پست‌های موجود در هرکدام باشد.

بعد هم با استفاده از شرط‌ها، جداکننده‌های هر آرشیو را مشخص کردیم. مثلا برای آرشیوهای زمانی، نام هر ماه در یک خط جدید باشد، یا برای نمایش تگ‌ها همه پشت سر هم و با جداکننده‌ی - باشند.

**خطوط ۱۰ تا ۱۵**: گفتیم که مقدار هر آرشیو لیستی است که utid پست‌هایی که در آن دسته بندی هستند را هم در خود دارد، بین این خطوط مشخص کردیم تیتر و لینک تمام نوشته‌هایی که در دسته بندی هستند، زیر نام آن دسته بندی نمایش داده شوند.با استفاده از ENTRIES.$utid تمام کارهایی که برای نمایش پست ها با POSTS انجام میدادیم را میتوان انجام داد، مثلا خلاصه‌ی متن را لود کرد:

	ENTRIES.$utid.body.less

#### روش دوم، نمایش دادن با ترتیب دلخواه
روش بالا روش خوبی است، مخصوصا برای زمانی که میخواهیم از یک قالب به شکل مشترک استفاده کنیم اما قدرت کنترل و انعطاف کمی دارد، مثلا شاید بخواهیم در یک سایت آرشیو زمانی در ابتدای ستون کناری باشد و در یک سایت در انتها. در این روش میتوانیم هر آرشیو را هرکجا که بخواهیم لود کنیم. کافی است حلقه‌ای با نام آرشیو و پسوند آرشیو با حروف بزرگ را لود کنیم:

	{{ IF CATEGORIES_ARCHIVE }}
	<h3>categories archive</h3>
	{{ FOREACH cat IN CATEGORIES_ARCHIVE }}
	  <a href="{{ cat.url }}">{{ cat.name }}</a> - <small>{{ cat.posts.size }}</small><br>
	{{ END }}
	{{ END }}
	<hr>

**نکته‌**: همانطور که در مثال قبل هم گفتیم، لیست‌های آرشیو علاوه بر نام و آدرس، پست‌هایی که در دسته بندیشان قرار میگیرد را هم در خود دارند، در مثال قبل با استفاده از posts مقدار utid ها را به دست آوردیم و در ENTRIES لود کردیم، اینجا فقط تعدادشان را گرفتیم و مشخص کردیم در هر دسته بندی چه تعداد نوشته داریم. {{ cat.posts.size }}

برای نمایش کامل تمام آرشیوها در این مثال باید از کد زیر استفاده کرد، در این مثال هم در قسمت category تمام پست ها را با استفاده از utid نمایش می‌دهیم:

	{{ IF CATEGORIES_ARCHIVE }}
	<h3>categories archive</h3>
	{{ FOREACH cat IN CATEGORIES_ARCHIVE }}
	   <a href="{{ cat.url }}">{{ cat.name }}</a> - <small>{{ cat.posts.size }}</small><br>
	{{ END }}<hr>
	{{ END }}
	
	{{ IF CATEGORY_ARCHIVE }}
	<h3>category archive</h3>
	{{ FOREACH cat IN CATEGORY_ARCHIVE }}
	  <a href="{{ cat.url }}">{{ cat.name }}</a> - <small>{{ cat.posts.size }}</small><br>
		<br>
		{{ FOREACH utid IN cat.posts }}
			&nbsp;&nbsp;-&nbsp;<a href="{{ ENTRIES.$utid.url }}">{{ ENTRIES.$utid.title }}</a><br>
		{{ END }}
	{{ END }}
	<hr>
	{{ END }}
	
	{{ IF TAGS_ARCHIVE }}
	<h3>categories archive</h3>
	{{ FOREACH tag IN TAGS_ARCHIVE }}
	  <a href="{{ tag.url }}">{{ tag.name }}</a> - <small>{{ tag.posts.size }}</small><br>
	{{ END }}
	<hr>
	{{ END }}
	
	{{ IF AUTHOR_ARCHIVE }}
	<h3>author archive</h3>
	{{ FOREACH author IN AUTHOR_ARCHIVE }}
	  <a href="{{ author.url }}">{{ author.name }}</a> - <small>{{ author.posts.size }}</small><br>
	{{ END }}
	<hr>
	{{ END }}
	
	{{ IF DATE_ARCHIVE }}
	<h3>date archive</h3>
	{{ FOREACH date IN DATE_ARCHIVE }}
	  <a href="{{ date.url }}">{{ date.name }}</a> - <small>{{ date.posts.size }}</small><br>
	{{ END }}
	<hr>
	{{ END }}
	
	{{ IF JDATE_ARCHIVE }}
	<h3>jalali archive</h3>
	{{ FOREACH date IN JDATE_ARCHIVE }}
	  <a href="{{ date.url }}">{{ date.name }}</a> - <small>{{ date.posts.size }}</small><br>
	{{ END }}
	<hr>
	{{ END }}

یکی از دو روش بالا را انتخاب کنید، سپس کدهای نوشته شده را در قالب‌های post, index و archive کپی کنید

	<!-- sidebar -->
	<td width="30%">
	   >>> اینجا کپی کنید
	</td>

در فایل‌های مثال که برای دانلود کردن آماده شده از روش اول در قالب archive و روش دوم برای index و post استفاده شده.
