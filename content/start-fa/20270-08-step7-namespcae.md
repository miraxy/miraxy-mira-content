---
utid: 20270
date: 2017-04-01 15:24:12
title: تغییر آدرس آرشیو‌ها
_index: namespcae
chapter: 08
chaptername: گام هفتم: شخصی سازی بیشتر
---
دیدیم که در تنظیم کردن هر سایت برای آدرس‌دهی به هر پست می‌توانیم از مشخصات آن پست استفاده کنیم، برای مثال:

	permalink: :category/:title.html
	یا
	permalink: :author/:year/:title

حالا ممکن است دسته بندی موضوعی به نام **آموزشی** داشته باشیم، آدرس ثابت با استفاده از مدل اول این خواهد بود:

	SITE_ADDRESS.com/آموزش/post-title.html

و اگر آرشیوی بر اساس category ساخته باشیم هم آدرس مطالب دسته بندی **آموزشی** این خواهد بود:

	SITE_ADDRESS.com/category/آموزش/

یا نام نویسنده مطلب محمد محمدی باشد، در مدل دوم آدرس شبیه به این ساخته خواهد شد:

	SITE_ADDRESS.com/محمد-محمدی/post-title/

و آدرس آرشیو این نویسنده:

	SITE_ADDRESS.com/author/محمد-محمدی/

یا اینکه یک دسته بندی با نام طولانی داشته باشیم، مثلا نام دسته بندی این نام باشد: learn use vim in gnu linux systems  
آدرسذها این شکلی خواهتد بود:

	SITE_ADDRESS.com/learn-use-vim-in-gnu-linux-systems/post-title.html
	و 
	SITE_ADDRESS.com/category/learn-use-vim-in-gnu-linux-systems/

شاید استفاده از نام‌های طولانی یا حروف فارسی در آدرس را دوست نداشته باشید یا سروری که از آن استفاده می‌کنید محدودیت داشته باشد برای پذیرفتن نام‌های غیر لاتین. راه حل استفاده از namespace در فایل کانفیگ عمومی یا اختصاصی هر سایت است.

حالا برای تمرین این مثال، در وبلاگ فارسی یک نوشته جدید به جود بیاورید و در قسمت category مقدار آزمایش را وارید کنید.

	---
	utid: 20170326160744
	date: 2017-03-26 16:07:44
	title: فضای نام
	_index: namespace
	category: آزمایش
	---

آدرسی که به این پست اختصاص داده می‌شود:

	YOUR_ADDRESS.COM/آزمایش/a2017/03/26/namespace.html

حالا اگر میخواهید از فضای نام‌ها تمام سایت‌ها به شکل عمومی استفاده کنند در فایل config.yml و اگر میخواهید تنها در وبلاگ فارسی این فضای نام فعال باشد در فایل config/blog-fa.yml فیبدی به نام namespace را به این شکل به وجود بیاورید:

	namespace:
	  آزمایش: test
	  آموزش: learn
	  کتاب: book
	  شخصی: personal
	  عمومی: general
	  محمد محمدی: mohamad mohamadi

از این به بعد میرا هرجا با یکی از این‌ها در آرشیو مواجه شود، برای ساختن آدرس آن از نام اختصاصی‌اش در فضای نام‌ها استفاده می‌کند. مثلا پست آزمایشی که کمی‌قبل‌تر ساختیم، آدرسی مشابه این آدرس خواهد گرفت:

	YOUR_ADDRESS.COM/test/2017/03/26/namespace.html
	و آدرس آرشیو:
	SITE_ADDRESS.com/category/test/

یا اگر دسته بندی **کتاب** داشته باشیم:

	YOUR_ADDRESS.COM/book/2010/10/10/post-title.html
	SITE_ADDRESS.com/category/book/
