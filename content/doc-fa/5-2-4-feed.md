---
utid           : 000500020004
title          : feed
chapter        : 5
chaptername    : پوسته
seassion       : 2
seassionname   : برچسب‌های مورد استفاده در پوسته
---


<p>به شکل پیش‌فرض از پوسته atom.tt2 برای ساخته شدن خوراک سایت استفاده می‌شود، اما می‌توانید نام این پوسته را در تنظیمات تغییر دهید.</p>

<p>به جز برچسب UTIDS تمام برچسب‌های main.tt2 در index و feed با همان مقادیر معتبر هستند</p>

<pre><code>{{ MianTITLE }}
{{ MianDESCRIPTION }}
{{ MianURL }}
{{ MianROOT }}
{{ MianSTATIC }}
{{ MainIMAGEURL }}
{{ MianAUTHOR }}
{{ MianEMAIL }}

{{ PageTITLE }}
   site title

{{ TITLE }}
{{ DESCRIPTION }}
{{ URL }}
{{ ROOT }}
{{ STATIC }}
{{ IMAGEURL }}
{{ AUTHOR }}
{{ EMAIL }}

{{ ARCHIVES }}

{{ ENTRIES }}
{{ FLOORS }}
{{ POSTS }}
{{ IS_FEED }} :(boolean) true

{{ MAIN }}
{{ SITE }}
{{ BUILD }}
</code></pre>


