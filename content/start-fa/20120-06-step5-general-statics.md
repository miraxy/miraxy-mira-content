---
utid: 20120
date: 2017-03-28 12:55:39
title: ضمیمه‌های عمومی
_index: general-statics
chapter: 06
chaptername: گام پنجم: فایل‌ها و پوشه‌های ضمیمه یا statics
---
هنگام استفاده از میرا، در مسیر statics در شاخه‌ی اصلی که پیکربندی شده، فایل‌های ثابت و ضمیمه‌ی عمومی را می‌توانید نگهداری کنید.

`~/mira/statics`
محتویات این پوشه به مسیری که در فایل تنظیمات
`~/mira/config.yml`
و فیلد static مسیر دهی کرده‌اید منتقل می‌شود و در قالب با استفاده از کد
`{{ MainSTATIC }}`
یا
`{{ MAIN.static }}`
قابل دسترسی خواهد بود.

برای مثال اگر فیلد static در فایل config.yml مساوی
`/attach`
باشد و سایت‌مان را قرار باشد در address.com منتشر کنیم، نتیحه مسیری شبیه به این خواهد بود:

	~/mira/config.yml  >       static: /attach
	 ‌
	~/mira/statics     >       http://address.com/attach/

#### دانلود [شاخه عمومی statics](https://raw.githubusercontent.com/miraxy/sample/master/statics.zip) 
