---
utid           : 000500020008
title          : نمایش فیلدهای استفاده شده در config عمومی و اختصاصی
chapter        : 5
chaptername    : پوسته
seassion       : 2
seassionname   : برچسب‌های مورد استفاده در پوسته
---


<p>تمام مقادیری که در config ذخیره شده‌اند در پوسته قابل استفاده هستند. مقادیر موجود در config.yml با استفاده از برچسب {{ MAIN }} در تمام قسمت‌ها قابل دسترسی است و فایل‌های پیکربندی ذخیره شده در دایرکتوری config هنگام ساخته شدن صفحات هر طبقه با برچسب {{ SITE }} در دسترس هستند. تمام برچسب‌هایی که به شکل پیش فرض در میرا هستند و از مقادیر config استفاده میکنند با استفاده از این برچسب نیز قابل مشاهده هستند، مانند {{ MainTITLE }} که برابر {{ MAIN.title }} است یا {{ TITLE }} که با {{ SITE.title }} نیز قابل دسترسی است.</p>

<pre><code>{{ MAIN.title }}
{{ MAIN.other }}
{{ SITE.author }}
{{ SITE.language }}
</code></pre>

<p>همچنین میتوان به آرایه‌ها و لیست‌ها را نیز با استفاده از این برچسب‌ها نمایش داد. برای مثال اگر در فایل پیکربندی اختصاصی یکی از سایت‌ها در دایرکتوری config لیستی برای علاقه‌مندی‌های نویسنده ساخته شده باشد:</p>

<pre><code>/config/blog.yml:

faves:
 - icecream
 - football
 - cinema
</code></pre>

<p>این لیست در پوسته به این صورت قابل دسترسی است:</p>

<pre><code>{{ FOREACH fave IN SITE.faves }}
   {{ fave }}
{{ END }}
</code></pre>

<p>یا اگر کلید مقداری از لینک شبکه‌های اجتماعی که نویسنده در آن‌ها عضو است در config.yml داشته باشیم:</p>

<pre><code>social:
 - name: twitter
   link: https://twitter.com/NAME
   desc: Follow me on

 - name: github
   link: https://github.com/NAME
   desc: Fork me on

 - name: instagram
   url: https://instagram.com/NAME
   desc: Follow me on
</code></pre>

<p>به این شکل از آن‌ها در پوسته می‌توان استفاده کرد:</p>

<pre><code>{{ FOREACH social IN MAIN.social }}
   {{ social.desc }} &lt;a href={{ social.link }}&gt;{{ social.name }}&lt;/a&gt;
{{ END }}
</code></pre>

