---
utid: 20070
date: 2017-03-28 11:41:43
title: تنظیمات اختصاصی برای هر سایت
_index: specific-config
chapter: 04
chaptername: گام سوم: تنظیم پیکربندی یا کانفیگ کردن
---
**می‌خواهیم هر کدام از این چهار سایت را در این آدرس‌ها منتشر کنیم:**

- وبلاگ فارسی: address.com/blog
- وبلاگ انگلیسی: address.com/en
- داستان دنباله‌دار: address.com/story
- آموزش لینوکس: address.com/linux

برای این منظور باید فیلدهای url و root را مقدار دهی کنیم.

در مورد **آدرس نهایی هر پست**:  
به یاد داشته باشید آدرس‌ها میتوانند به شکل پوشه یا فایل تولید شوند، برای دیدن تفاوت این دو مورد، در پایان گام تنظیمات، تفاوت فیلد permalink در فایل‌های تنظیمات وبلاگ فارسی با سایر سایت‌ها را ببینید.

- تصمیم داریم نوشته‌های وبلاگ فارسی در آدرس‌هایی که براساس تاریخ انتشار و دسته بندی موضوعی تولید شده‌اند منتشر شوند و در آدرس نهایی category و تاریخ‌ها به شکل مسیر باشند و تیتر مطلب به شکل یک فایل باشد.
- پست‌های وبلاگ انگلیسی از تاریخ انتشار در آدرس ثایت استفاده کنند. آدرس به شکل یک مسیر باشد.
- برای داستان‌ها تنها نام داستان در آدرس باشد. آدرس به شکل یک مسیر باشد.
- در آموزش لینوکس، در آدرس‌ هر پست نام نویسنده هم ذکر شده باشد. آدرس به شکل یک مسیر باشد.
برای تنظیم این موارد در فایل تنظیمات فیلد permalink را باید مقدار دهی کنیم

**لیست‌های آرشیوی مورد نظرمان:**

- برای وبلاگ فارسی category و آرشیو زمانی بر اساس تاریخ شمسی
- برای وبلاگ انگلیسی tags و آرشیو زمانی بر اساس تاریخ میلادی
- برای داستان هیچ لیست آرشیوی در نظر نداریم
- و در آموزش هم tags, categories, author

برای این‌کار باید فیلد lists را مقدار دهی کنیم.

**نمایش تعداد نوشته‌ها در هر صفحه:**

 - برای وبلاگ‌های فارسی و انگلیسی، در صفحه اول میخواهیم ۵ نوشته آخر نوشته شده باشند، و در صفحات آرشیو هم تیتر ۱۰ نوشته آخر در هر صفحه باشد.
 - برای آموزش‌ها میخواهیم در صفحه اصلی ۱۰ نوشته آخر نمایش داده شوند و در صفحات آرشیو تمام پست‌ها در یک صفحه برای هر آرشیو باشند.
 - برای داستان دنباله دارمان هم میخواهیم تمام داستان‌هایی که تا به حال نوشته‌ایم در همان صفحه اول باشند، و ترتیب نمایششان هم برعکس باشد، به این ترتیب که نوشته‌های قدیمی‌تر در بالا باشند.

برای نمایش تعداد هر پست در صفحه اول به فیلد post_num مقدار دهی میکنیم و برای تعداد پست‌ها در هر صفحه آرشیو هم archive_post_num  
برای ترتیب نمایش هم فیلد post_sort 

**فایل‌های ضمیمه** وبلاگ‌های فارسی و انگلیسی را هم در زیر شاخه‌ی آدرس خودشان در شاخه‌ی assets می‌خواهیم ذخیره کنیم، اما ضمیمه‌های آموزش لینوکس و داستان را در زیرشاخه‌ی آدرس خود سایت اما در شاخه‌ی static.

در آخر برای هر سه سایتی که به فارسی مینویسیم می‌خواهیم تاریخ هجری شمسی را هم داشته باشیم، برای این منظور باید پلاگین Jdate را فعال کنیم. و در وبلاگ فارسی آرشیو بر اساس تاریخ شمسی هم می‌خواهیم داشته باشیم.

برای تنظیمات عمومی فایل config.yml در ریشه اصلی از قبل موجود است، برای ذخیره کردن تنظیمات مشخص شده برای هر سایت هم، در دایرکتوری config هم‌نام با نام هر سایت در شاخه یک فایل جدید با پسوند yml میسازیم

	~/mira/config/blog-fa.yml
	~/mira/config/blog-en.yml
	~/mira/config/story.yml
	~/mira/config/linux-learn.yml

با توجه به تمام مواردی که در بالا برای تنظیمات در نظر گرفتیم هر کدارم از این چهار فایل باید اینگونه باشند:

`~/mira/config/blog-fa.yml`

	title: وبلاگ فارسی من
	description: اینجا وبلاگ فارسی من است
	url: http://www.address.com/blog/
	root: /blog/
	static: /blog/assets
	imageurl: /blog/assets/article_images
	permalink: :category/:year/:month/:day/:title.html
	post_num: 5
	archive_post_num: 10
	lists:
	 - category
	 - jdate
	plugins:
	 - Jdate
	lang: fa


`~/mira/config/blog-en.yml`

	title: my english blog
	description: this is my english blog

	url: http://www.address.com/en/
	root: /en/
	static: /en/assets
	imageurl: /en/assets/images
	permalink: :year/:month/:day/:title/
	post_num: 5
	archive_post_num: 10
	lists:
	 - tags
	 - date
	lang: en


`~/mira/config/story.yml`

	title: دنباله دار
	description: توضیحاتی در مورد داستان دنباله دار من
	url: http://www.address.com/story/
	root: /story/
	static: /story/static
	imageurl: /story/static/images
	permalink: /:title/
	post_num: all
	post_sort: reverse
	lists:
	plugins:
	 - Jdate
	lang: fa


`~/mira/config/linux-learn.yml`

	title: آموزش لینوکس
	description: مطالبی که روزانه در مورد لینوکس یاد میگیریم و دوست داریم با دیگران به اشتراک بگذاریم

	url: http://www.address.com/linux/
	root: /linux/
	static: /linux/static
	imageurl: /linux/static/images
	permalink: :author/:title/
	default_markup: markdown
	post_num: 10
	archive_post_num: all
	lists:
	 - categories
	 - tags
	 - author
	plugins:
	 - Jdate
	lang: fa

به فایل تنظیمات سایت «دنباله دار» نگاه کنید، فیلد lists وجود دارد، اما به آن مقداری داده نشده، این یعنی میخواهید هیچ آرشیوی نداشته باشید، اگر فیلد lists را به جای خالی رها کردن، کلا در تنظیمات وارد نمی‌کردیم، به معنی وجود نداشتن هیچ آرشیوی نیست، بلکه به این معنی بود که هر مقداری که فایل تنظیمات عمومی برای آرشیو در خود دارد برای این سایت هم همان مقدار در نظر گرفته شود.

همانطور که میبینید در هیچ کدام از فایل‌های تنظیم اختصاصی template و default_markup وجود ندارد، اما در فایل تنظیمات عمومی، config.yml در شاخه‌ی اصلی این فیلد هم وجود دارد و هم مقدار دارد، وجود نداشتن یک فیلد در **تنظیمات اختصاصی** به این معنی است که می‌خواهیم برای آن فیلد از تنظیمات عمومی پیروی کنیم. پس مقدار my-theme و markdown در config.yml، برای تمام سایت‌ها معتبر است.

**نکته:** در تنظیمات وبلاگ انگلیسی فیلدی را اضافه کرده‌ایم برای مشخص کردن زبان
`lang: en`
و در سایر سایت‌ها
`lang: fa`
این یک فیلد شخصی است که در تنظیمات هیچ تعریف مشخصی ندارد و روی تنظیمات تاثیری نمی‌گذارد، این فیلد را برای استفاده در قالب نهایی در آینده نوشته‌ایم، فعلا کاری با آن نداریم.

