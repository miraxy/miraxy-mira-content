---
utid: 20240
date: 2017-03-28 20:00:43
title: پوسته‌های بیشتر برای هر قالب و تغییر آدرس
_index: more templates
chapter: 07
chaptername: گام ششم: ساختن قالب
---
پیش از این گفتیم که علاوه بر پنج فایل پایه‌ی هر قالب، میتوان به هر تعداد دیگر پوسته برای یک قالب تعریف کرد. در میرا می‌توان برای هر آرشیو یا هر پست یک قالب مجزا داشت.

#### پوسته‌های متفاوت برای هر آرشیو

برای داشتن پوسته‌ی متفاوت برای هر آرشیو، کافی است هم‌نام با آن آرشیو یک فایل در دایرکتوری قالب‌مان داشته باشیم.

برای مثال اگر بخواهیم پوسته‌ی آرشیو category با سایر آرشیوها مثل tags یا آرشیوزمانی و... متفاوت باشد، تنها کافی است در دایرکتوری قالب، یک فایل جدید به نام category.tt2 بسازیم، از این به بعد در هر سایت که آرشیوی به این نام وجود داشت، به جای استفاده از archive.tt2، با استفاده از category.tt2 خروجی آن تولید می‌شود.

#### پوسته‌های متفاوت برای پست ها

گاهی اوقات نیاز داریم آدرس ثابت یک نوشته با سایر نوشته‌ها متفاوت باشد، مثلا برای ساختن page ها یا هر دلیل دیگر. برای این‌که به میرا بگوییم به جای post.tt2 از پوسته‌ی دیگری برای ساختن خروجی یک پست استفاده کند، باید در سربرگ آن پست به فیلد _layout مقدار بدهیم. برای مثال:

	_layout: custom_post_template

**نکته**:  
برخلاف سایر پوسته‌ها، برای صفحات تعریف شده به عنوان پوسته‌ی اختصاصی پست‌ها، الزامی به استفاده از پسوند tt2 برای ساختن پوسته نداریم. استفاده کردن از پسوند تنها در این حالت اختیاری است.


#### تغییر آدرس

همچنین می‌توان آدرس انتشار یک پست را از فرمت تعیین شده در فایل کانفیگ اختصاصی سایتی که در آن منتشر می‌شود جدا کرد. برای مثال در فایل blog-fa.yml به فیلد permalink این مقدار را داده بودیم:

	:year/:month/:day/:title.html

اما اگر در سربرگ هر کدام از پست‌ها فیلد _permalink را مقدار دهی کنیم، این مسیر تنها برای آن پست تغییر میکند:

	_permalink: :year/:title/
	یا
	_permalink: /:title/
	یا
	_permalink: some/thing/else/:title.php
