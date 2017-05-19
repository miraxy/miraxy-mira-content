---
utid           : 000500030012
title          : UTIDS
chapter        : 5
chaptername    : پوسته
seassion       : 3
seassionname   : توضیحاتی در مورد برچسب‌ها
---


<p>کلید نام تمام محتوای موجود در سایت مرتب شده بر اساس مقدار utid هر پست، برابر با utid هر پست، برای لود کردن محتوا در برچسب Entries قابل استفاده است.</p>

<p><strong>این برچسب تنها مختص به main.tt2 میباشد</strong></p>

<p>تمام مقادیر معتبر برای POSTS در زیر این برچسب با اضافه کردن ENTRIES.$id نیز قابل استفاده هستند
نحوه‌ی استفاده به همراه ENTRIES</p>

<pre><code>{{ FOREACH id IN UTIDS }}
   &lt;h2&gt;&lt;a href="{{ ENTRIES.$id.url }}"&gt;{{ ENTRIES.$id.title }}&lt;/a&gt;&lt;h2&gt;
   &lt;h4&gt;{{ ENTRIES.$id.CALENDAR.day }}-{{ ENTRIES.$id.CALENDAR.month_name }}-{{ ENTRIES.$id.CALENDAR.year }}&lt;/h4&gt;
   &lt;p&gt;{{ ENTRIES.$id.body.less }}&lt;/p&gt;
{{ END }}
</code></pre>

<p><br><br></p>


