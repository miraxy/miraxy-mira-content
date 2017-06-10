---
utid          : 2017061021032404020006
title         : index.tt2
season        : 4
seasonname    : پوسته
chapter       : 2
chaptername   : برچسب‌های مورد استفاده در پوسته
---


<pre><code>{{ MianTITLE }}
{{ MianDESCRIPTION }}
{{ MianURL }}
{{ MianROOT }}
{{ MianSTATIC }}
{{ MainIMAGEURL }}
{{ MianAUTHOR }}
{{ MianEMAIL }}

{{ PageTITLE }}
   "post title - site title"

{{ PostTITLE }}
   "post title"

{{ TITLE }}
{{ DESCRIPTION }}
{{ URL }}
{{ ROOT }}
{{ STATIC }}
{{ IMAGEURL }}
{{ AUTHOR }}
{{ EMAIL }}

{{ ARCHIVES }} :
برای اطلاعات کامل‌تر در مورد آرشیو ها قسمت اول بخش پوسته ها را ببینید، این برچسب مناسب برای نمایش در سایدبار و امثال آن است. برای ساختن صفحات آرشیو، archive.tt2 جهت نمایش محتوا، از POSTS استفاده می‌شود، کارکرد این برچسب با صفحات archive متفاوت است.

{{ ENTRIES }}
{{ FLOORS }}
{{ POSTS }}

{{ IS_POST }} :(boolean) true

if _type: page then:
{{ IS_POST }} :(boolean) false
{{ IS_PAGE }} :(boolean) true

{{ MAIN }}
{{ SITE }}
{{ BUILD }}
{{ PAGE }}

{{ post.* }}
</code></pre>

<p>در الگوی post.tt2 یا الگوی شخصی سازی شده صفحه‌ها نیازی به فراخوانی حلقه‌ی FOREACH POSTS نیست، تمام مقادیر مورد نیاز در  {{ post }} از پیش لود شده است. اما در صورت نیاز میتوانید این حلقه را هم لود کنید. مقادیر زیر در این الگو برابر هستند:</p>

<pre><code>1: با لود کردن حلقه
&lt;div class="content"&gt;
{{ FOREACH entry IN POSTS }}
  &lt;div class="title"&gt;{{ entry.title }}&lt;/div&gt;
  {{ entry.body.more }}
{{ END }}
&lt;/div&gt;

2: بدون لود کردن حلقه
&lt;div class="content"&gt;
  &lt;div class="title"&gt;{{ post.title }}&lt;/div&gt;
  {{ post.body.more }}
&lt;/div&gt;
</code></pre>


