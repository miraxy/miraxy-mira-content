---
utid: 20130
date: 2017-03-28 12:56:32
title: ضمیمه‌های اختصاصی هر طبقه
_index: specific-statics
chapter: 06
chaptername: گام پنجم: فایل‌ها و پوشه‌های ضمیمه یا statics
---
در پوشه‌ی محتوای هر سایت در شاخه‌ی content هر پوشه‌ای که نامش با خط زیر یا همان آندرلاین _ شروع شود از نظر میرا یک پوشه‌ی ضمیمه به حساب می‌آید و تمام محتویات آن‌را بدون هیچ بررسی به مسیر اصلی سایت منتقل میکند.

یک مثال:  
در بخش تنظیمات برای وبلاگ فارسی(blog-fa) در فیلدهای url و root مسیر blog را برای انتشار مشخص کردیم، پس هر پوشه‌ای که در مسیر blog-fa با ـ شروع شود به عنوان ضمیمه در مسیر blog آدرس دهی میشود، به این مثال‌ها دقت کنید:

	~mira/content/blog-fa/_assets
	/blog/assets/

	~mira/content/blog-fa/_statics
	/blog/statics/

	~mira/content/blog-fa/deep/_image
	/blog/deep/image

	~mira/content/blog-fa/more/deep/folder/_attach
	/blog/more/deep/folder/attach

دقت داشته باشید قبل از رسیدن به پوشه‌ی ضمیمه، اگر فایل محتوایی موجود باشد، برای انتشار آماده می‌شود، تنها بعد از رسیدن به اولین شاخه‌ای که با _ شروع شده باشد، میرا دست از نفوذ به عمق شاخه‌ها می‌کشد. برای مثال مسیرهای زیر را در نظر بگیرید

	~mira/content/blog-fa/more/content.md
	~mira/content/blog-fa/more/deep/post.txt
	~mira/content/blog-fa/more/deep/folder/contetnt.md
	~mira/content/blog-fa/more/deep/folder/_attach
	~mira/content/blog-fa/more/deep/folder/_attach/post.markdown

میرا سه فایل اول را که قبل از رسیدن به
`~mira/content/blog-fa/more/deep/folder/_attach`
قرار دارند، برای انتشار بررسی و آماده می‌کند، اما فایل آخر
`~mira/content/blog-fa/more/deep/folder/_attach/post.markdown`
را به عنوان یک فایل ضمیمه می‌شناسد و تنها آن را همان شکلی که هست به مسیر انتشار انتقال می‌دهد.

**نکته**:  
احتمالا متوجه شدید که فیلد static در فایل تنظیمات اختصاصی هیچ تاثری در انتقال و آدرس‌دهی به مسیر فایل‌ها و پوشه‌های ضمیمه برای سایت‌ها ندارد.

این فیلد تنها جهت سهولت دسترسی در قالب و استفاده در قالب سایت با تگ
`{{ STATIC }}`
یا
`{{ SITE.static }}`
می‌باشد.

#### اگر فایل مثال برای content را دانلود کرده باشید، محتوای اختصاصی static هر سایت، همراه با فایل content دانلود شده
