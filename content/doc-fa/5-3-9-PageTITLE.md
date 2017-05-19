---
utid           : 000500030009
title          : PageTITLE
chapter        : 5
chaptername    : پوسته
seassion       : 3
seassionname   : توضیحاتی در مورد برچسب‌ها
---


<p>تیتر صفحه، در صورتیکه از ماژولی شبیه به header برای لود کردن قسمت بالایی صفحات html به شکل ثابت در تمام صفحات استفاده کنید این برچسب کمک بسیاری برای تگ &lt;title&gt; خواهد کرد، برای مثال در main.tt2 مقداری برابر TITLE و در index.tt2 مساوی FloorTITLE خواهد داشت
نحوه‌ استفاده:</p>

<pre><code>{{ PageTitle }}
</code></pre>

<p>این برچسب در هر یک از پوسته‌ها مقدار متفاومتی را باز می‌گرداند:</p>

<p>main: <br />
تیتر ذخیره شده در فیلد title در فایل config.yml</p>

<p>index , feed: <br />
تیتر ذخیره شده در فیلد title در فایل پیکربندی اختصاصی در دایرکتوری config</p>

<p>field archive: <br />
تیتر اختصاصی سایت - نام فیلد آرشیو شده</p>

<p>date archive: <br />
تیتر اختصاصی سایت - سال / ماه</p>


