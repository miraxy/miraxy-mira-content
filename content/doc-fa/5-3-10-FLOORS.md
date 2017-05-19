---
utid           : 000500030010
title          : FLOORS
chapter        : 5
chaptername    : پوسته
seassion       : 3
seassionname   : توضیحاتی در مورد برچسب‌ها
---


<p>نام تمام طبقات موجود در سایت به همراه توضیحاتشان و تعداد مشخصی از پست‌ها که در فیلد post_num در فایل تنظیمات مشخص کرده‌اید</p>

<p>مقادیر موجود در این برچسب:</p>

<pre><code>name
description

posts (list)
</code></pre>

<p>فیلد posts شامل تعداد مشخص از آخرین ارسال‌های شماست، تعداد ارسال‌های موجود در این کلید از config.yml و فیلد post_num برداشت میشود. <br />
تمام مقادیری که برای POSTS که در قسمت‌های بعد توضیح داده میشود در مورد لیست posts در Floors نیز قابل استفاده است</p>

<p>نحوه‌ استفاده:</p>

<pre><code>{{ FOREACH site IN FLOORS.values }}
  {{ site.name }}
  {{ site.description }}

  {{ FOREACH post IN site.posts }}
    &lt;h2&gt;&lt;a href="{{ post.url }}"&gt;{{ post.title }}&lt;/a&gt;&lt;h2&gt;
    &lt;h4&gt;{{ post.CALENDAR.day }}-{{ post.CALENDAR.month_name }}-{{ post.CALENDAR.year }}&lt;/h4&gt;
    &lt;p&gt;{{ post.body.less }}&lt;/p&gt;
  {{ END }}

{{ END }}
</code></pre>


