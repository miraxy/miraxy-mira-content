---
utid           : 000300020017
title          : permalink
chapter        : 3
chaptername    : تنظیمات
seassion       : 2
seassionname   : فیلدهای قابل تنظیم
---


<p>مسیری که آدرس هر نوشته بر اساس آن ساخته خواهد شد.</p>

<pre><code>:year
سال انتشار پست
:month
ماه انتشار
:day
روز انتشار
:title
عنوان پست
:FIELD_NAME
نام هر فیلدی که محتوای تک خطی داشته باشد(لیست نباشد) و در هدر فایل پست با مقدار معتبر وجود داشته باشد

/some/thing/else
هرچیزی که بخواهید به آدرس شما اضافه شود
</code></pre>

<p>مثال:</p>

<pre><code>/a/:year/abcd/:month/:chapter/wxyz/:day/else/:title
که در اصل هر نوشته در آدرسی شبیه به آدرس زیر منتشر خواهد شد:
mysite.com/a/2017/abcd/02/session_4/wxyz/25/else/post_title_or_index/
</code></pre>

<p>همچنین میتوانید مشخص کنید که آدرس به صورت مسیر یا فایل خروجی ساخته شود. در صورتیکه در انتها مقدار .html یا هر پسوند دیگری که مایل باشید را مشخص کنید، آدرس به صورت یک فایل خواهد بود</p>

<pre><code>/:year/:month/:day/:category/:title.html
که در اصل هر نوشته در آدرسی شبیه به آدرس زیر منتشر خواهد شد:
mysite.com/2017/02/25/daily/post_title_or_index.html
</code></pre>


