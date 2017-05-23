---
utid          : 000400020007
title         : نمایش نوشته‌ها با حلقه‌ی POSTS
seassion      : 4
seassionname  : پوسته
chapter       : 2
chaptername   : برچسب‌های مورد استفاده در پوسته
---


<p>جهت نمایش نوشته‌ها از حلقه‌ای که اجزای POSTS را لود میکند میتوان استفاده کرد</p>

<pre><code>{{ FOREACH entry IN POSTS }}
    ...
{{ END }}
</code></pre>

<p>از این حلقه در صفحات index و archive میتوان استفاده کرد، همچنین در صفحه‌ی هر پست در پوسته post.tt2 نیز استفاده از این حلقه به شکل اختیاری معتبر است. در post.tt2 اگر این حلقه لود نشود هم تمام مقادیر با استفاده از کلید post معتبر هستند.</p>

<pre><code>{{ FOREACH post IN posts }}
   {{ post.title }} تیتر
   {{ post.url }} آدرس شناور
   {{ post.furl }} آدرس مطلق
   {{ post.body.less }} خلاصه متن
   {{ post.body.more }} متن کامل
   {{ post.date }} تاریخ کامل انتشار
   {{ post.CALENDAR.year }} سال انتشار
   {{ post.CALENDAR.month }} ماه انتشار به شکل عددی
   {{ post.CALENDAR.month_name }} نام ماه
   {{ post.CALENDAR.month_abbr }} خلاصه نام ماه
   {{ post.CALENDAR.day }} روز انتشار به شکل عددی
   {{ post.CALENDAR.day_name }} نام روز
   {{ post.CALENDAR.day_abbr }} خلاصه نام روز
   اگر از پلاگین jdate هم استفاده کرده باشید
   {{ post.jdate }}
   {{ post.CALENDAR.jyear }} سال انتشار
   {{ post.CALENDAR.jmonth }} ماه انتشار به شکل عددی
   {{ post.CALENDAR.jmonth_name }} نام ماه
   {{ post.CALENDAR.jday }} روز انتشار به شکل عددی
   {{ post.CALENDAR.jday_name }} نام روز
   سایر فیلدها
   {{ post.other }}
   {{ post.another }}
   در صورتیکه فیلدهایی را به صورت لیستی نوشته باشید، مثلا نام منابع در صورتیکه نوشته بیش از یک منبع داشته باشد:
   {{ FOREACH source in post.sources }}
      {{ source }}
   {{ END }}
   اگر فیلدی را آرشیو کرده باشید، چه آن فیلد لیست باشد چه نباشد باید در حلقه لود شود
   {{ FOREACH cat in post.categories }}
    {{ cat.url }} آدرس شناور
    {{ cat.furl }} آدرس مطلق
    {{ cat.name }} نام آرشیو
    {{ cat.showname }} namespace
   {{ END }}
</code></pre>


