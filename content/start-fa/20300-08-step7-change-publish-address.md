---
utid: 20300
date: 2017-04-06 00:49:59
title: تغییر آدرس انتشار سایت‌ها
_index: change publish address
chapter: 08
chaptername: گام هفتم: شخصی سازی بیشتر
---
در تنظیمات دیدیم که ریشه‌ی اصلی سایت را برای یک صفحه‌ی مشترک بین تمام سایت‌ها در نظر گرفتیم و بعد برای هر سایت یک آدرس در لول پایینتر مشخص کردیم:

	your-address.com/          >    صفحه مشترک بین هر چهار سایت
	your-address.com/blog/     >    وبلاگ فارسی
	your-address.com/en/       >    وبلاگ انگلیسی
	your-address.com/story/    >    داستان‌ها
	your-address.com/linux/    >    آموزش لینوکس

اما شاید بخواهید ریشه اصلی سایت را برای وبلاگ فارسی در نظر بگیرید و صفحه‌ی مشترک را در زیر آدرس دیگری بسازید، مثل این:

	your-address.com/main/     >    صفحه مشترک بین هر چهار سایت
	your-address.com/          >    وبلاگ فارسی

برای این منظور config.yml و config/blog-fa.yml را ویرایش کنید و url و root را تغییر دهید:

`config.yml`

	url: your-address.com/main
	root: /main

`config/blog-fa.yml`

	url: your-address.com/
	root: /

یا شاید اصلا نخواهید صفحه‌ی مشترک را داشته باشید، برای اینکار url و root را در config.yml با مقدار url و root در config/blog-fa.yml یکی قرار دهید. در صورت مساوی شدن مقدار این دو فیلد بین main و طبقات، اولویت با طبقات است. در این صورت دیگر صفحه مشترکی نخواهید داشت. میتوانید main.tt2 را هم از قالبتان پاک کنید.

`config.yml`

	url: your-address.com/
	root: /

`config/blog-fa.yml`

	url: your-address.com/
	root: /



