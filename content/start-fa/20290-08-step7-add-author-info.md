---
utid: 20290
date: 2017-04-01 22:01:50
title: افزودن مشخصات نویسنده مطلب
_index: add author info
chapter: 08
chaptername: گام هفتم: شخصی سازی بیشتر
---
اگر به یاد داشته باشید در سایت آموزش لینوکس، بیشتر از یک نویسنده برای مطالبمان داشتیم، حالا میخواهیم یک اطلاعات کلی از هرکدام را به سایدبار در زیر آرشیو نام‌هایشان اضافه کنیم، ابتدا linux-learn.yml را ویرایش میکنیم و خطوط زیر را در آن می‌نویسیم:

	authors:
	 -
	  name: farbodgame
	  desc: توضیحاتی در مورد کاربر
	  twitter: twitter.com/TWITTER_USER_NAME
	 -
	  name: MrNull
	  desc: توضیحاتی در مورد کاربر
	  twitter: twitter.com/TWITTER_USER_NAME
	 -
	  name: rmasoumvand
	  desc: توضیحاتی در مورد کاربر
	  twitter: twitter.com/TWITTER_USER_NAME

> به فاصله‌ها دقت کنید، هر بخش که داخل رفتیم، یک خط فاصله اضافه شده است، authors در ابتدای خط است، قبل از هر خط تیره - یک space وجود دارد و یک مرحله فرورفتگی ایجاد شده و بعد، قبل از name، desc و twitter دو خط فاصله یا همان space هست، یعنی دو مرحله فرورفتگی.

بعد قالب index.tt2 را باز کنید و در sidebar، بلوک کد {{ IF AUTHOR_ARCHIVE }} را پیدا کنید و به جای آن کدهای زیر را کپی کنید:

	{{ IF AUTHOR_ARCHIVE }}
	<h3>author archive</h3>
	{{ FOREACH author IN AUTHOR_ARCHIVE }}
	  <a href="{{ author.url }}">{{ author.name }}</a> - <small>{{ author.posts.size }}</small>
	<!-- این قسمت به کد اضافه شده است -->
	  {{ IF SITE.authors }}
	  {{ FOREACH auth IN SITE.authors }}
	  {{ IF author.name == auth.name }}
		<ul>
		<li>{{ auth.desc }}</li>
		<li><a href="{{ auth.twitter }}">twitter</a></li>
		</ul>
	  {{ END }}
	  {{ END }}
	  {{ END }}
	<!-- تا اینجا -->
	{{ END }}
	<hr>
	{{ END }}
