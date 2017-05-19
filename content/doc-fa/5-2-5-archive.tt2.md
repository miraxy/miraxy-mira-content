---
utid           : 000500020005
title          : archive.tt2
chapter        : 5
chaptername    : پوسته
seassion       : 2
seassionname   : برچسب‌های مورد استفاده در پوسته
---


<p>به جز برچسب UTIDS تمام برچسب‌های main.tt2 و index.tt2 در archive با همان مقادیر معتبر هستند</p>

<pre><code>{{ MainTITLE }}
{{ MainDESCRIPTION }}
{{ MainURL }}
{{ MainROOT }}
{{ MainSTATIC }}
{{ MainIMAGEURL }}
{{ MainAUTHOR }}
{{ MainEMAIL }}

{{ PageTITLE }}
   title - YYYY/MM     :if dae archive
   title - field name  :if field archive

{{ TITLE }}
{{ DESCRIPTION }}
{{ URL }}
{{ ROOT }}
{{ STATIC }}
{{ IMAGEURL }}
{{ AUTHOR }}
{{ EMAIL }}

{{ ArchiveTITLE }} :
   YYYY/MM    :if dae archive
   field name :if field archive

{{ ENTRIES }}
{{ FLOORS }}
{{ POSTS }}

{{ MAIN }}
{{ SITE }}
{{ BUILD }}

{{ IS_ARCHIVE }}      :(boolean) true for field archives
{{ IS_DATE_ARCHIVE }} :(boolean) true for date archives

{{ ARCH }} : مشخصات آرشیوی که در حال ساخته شدن است
برای آرشیو زمانی:
   {{ ARCH.name }}       : october 2014   -    اردیبهشت 95
   {{ ARCH.year }}
   {{ ARCH.month }}
   {{ ARCH.month_name }}
   {{ ARCH.number }}     : year - month     2014 - 07         1395 - 11
   {{ ARCH.url }}        : float url      /site/archive/
   {{ ARCH.furl }}       : full url        http://example.org/site/archive/
برای آرشیو ساخته شده از فیلدهای پست:
   {{ ARCH.name }}
   {{ ARCH.showname }} : namespace
   {{ ARCH.url }}
   {{ ARCH.furl }}
</code></pre>

