---
utid: 20280
date: 2017-04-01 21:14:19
title: اضافه کردن لینک شبکه‌های اجتماعی
_index: add social links
chapter: 08
chaptername: گام هفتم: شخصی سازی بیشتر
---
برای افزودن لینک خودمان در شبکه‌های اجتماعی به جایی مثل ساید باز هم میرویم سراغ کانفیگ‌ها و اضافه کردن چند خط به هرکدامشان

فرض میکنیم لینکی که می‌خواهیم برای شبکه‌های اجتماعی در نظر بگیریم در تمام سایت‌ها ثابت نیست و برای هر سایت یک کانال، یا اکانت جدا در شبکه‌های اجتماعی و یک کانال در پیام رسان تلگرام را ساخته‌ایم.

از اینجای مثال فقط برای وبلاگ فارسی همه چیز را در نظر می‌گیریم، اما می‌توانید برای سه سایت دیگر هم به همین شکل کار را انجام دهید یا کلا این همه چیز را به جای تنظیم اختصاصی هر سایت در تنظیم‌های عمومی بگنجانید و در همه‌ی سایت‌ها از همان تنظیم استفاده کنید.

آدرس ها را هم این‌ها در نظر میگیریم:

#### وبلاگ فارسی:
twitter.com/@MY_FA_BLOG_MIRA
telegram.me/MY_FA_BLOG_MIRA

حالا به blog-fa.yml  کدهای زیر را اضافه می‌کنیم:

`~/mira/config/blog-fa.yml`

	socials:
	 -
	  name: twitter
	  url: https://twitter.com/MY_FA_BLOG_MIRA
	 -
	  name: instagram
	  url: https://instagram.com/MY_FA_BLOG_MIRA
	 -
	  name: github
	  url: https://github.com/MY_FA_BLOG_MIRA

> به فاصله‌ها دقت کنید، هر بخش که داخل رفتیم، یک خط فاصله اضافه شده است، socials در ابتدای خط است، قبل از هر خط تیره - یک space وجود دارد و یک مرحله فرورفتگی ایجاد شده و بعد، قبل از name و url دو خط فاصله یا همان space هست، یعنی دو مرحله فرورفتگی.

حالا در my-theme فایل index.tt2 را باز می‌کینم و هر کجا که خواستیم شبکه‌های اجتماعی را نمایش دهیم این کدها را به آن اضافه می‌کنیم، مثلا در بالاترین قسمت sidebar:

	<td width="30%" valign="top">
	{{ IF SITE.socials }}
		<h3>socials</h3>
		{{ FOREACH social IN SITE.socials }}
			<a href="{{ social.url }}">{{ social.name }}</a>>ذق<
		{{ END }}
	{{ END }}

برای هر کدام از چهار سایت دیگر هم می‌توان همین کار را تکرار کرد، یا اینکه برای همه سایت‌ها از یک آدرس مشترک در شبکه‌های اجتماعی استفاده کنیم و همه اطلاعات را در config.yml وارد کنیم، در این حالت برای نمایش لینک‌ها در سایت، به جای SITE.socials باید از MAIN.socials استفاده کرد.