---
utid          : 2017061021032404020002
title         : main.tt2
season        : 4
seasonname    : پوسته
chapter       : 2
chaptername   : برچسب‌های مورد استفاده در پوسته
---


<p>برچسب‌های معتبر در این پوسته و مقادیرشان.  </p>

<pre><code>{{ MainTITLE }}
{{ MainDESCRIPTION }}
{{ MainURL }}
{{ MainROOT }}
{{ MainSTATIC }}
{{ MainIMAGEURL }}
{{ MainAUTHOR }}
{{ MainEMAIL }}
{{ PageTitle }}
   main title
{{ IS_MAIN }} : boolean (true)

{{ FLOORS }}
</code></pre>

<p>تنها راه نمایش محتوا در صفحه‌ی main، استفاده از حلقه‌ی FLOORS به صورت مستقل، یا حلقه‌ی ENTRIES و کلیدهای UTIDS می‌باشد.</p>

<p>برای انتشار محتوا در هر سایت از حلقه‌ی POSTS استفاده خواهیم کرد، دقت کنید این حلقه در main معتبر نیست. اما posts به عنوان یک حلقه زیر مجموعه FLOORS معتبر است.</p>

<p>این حلقه تنها به اندازه‌ی مقداری که در فیلد post_num در فایل config.yml مشخص کرده‌اید از محتوای هر طبقه را در خود ذخیره می‌کند.
نحوه‌ استفاده:</p>

<pre><code>{{ FOREACH site IN FLOORS.values }}
  {{ site.name }}
  {{ site.description }}

  {{ FOREACH post IN site.posts }}
    &lt;h2&gt;&lt;a href="{{ post.url }}"&gt;{{ post.title }}&lt;/a&gt;&lt;h2&gt;
    &lt;h4&gt;{{ post.CALENDAR.day }}-{{ post.CALENDAR.month_name }}-{{ post.CALENDAR.year }}&lt;/h4&gt;
    &lt;p&gt;{{ post.body.less }}&lt;/p&gt;
  {{ END }}

  {{ IF site.SITE.language == 'farsi' }}
    &lt;a href="{{ site.url }}"&gt;ورود به صفحه اصلی&lt;/a&gt;
  {{ ELSE }}
    &lt;a href="{{ site.url }}"&gt;Main page&lt;/a&gt;
  {{ END }}

{{ END }}
</code></pre>

<p>و برچسب UTIDS</p>

<pre><code>{{ UTIDS }}
</code></pre>

<p>کلید نام تمام محتوای موجود در سایت مرتب شده بر اساس مقدار utid هر پست، برابر با utid هر پست، در UTIDS ذخیره شده، برای لود کردن محتوا در برچسب ENTRIES قابل استفاده است.</p>

<p>تمام محتوای تولید شده، نمایش داده خواهند شد، <strong>تمام محتوا</strong>، اگر در میرا پنج سایت(طبقه) ساخته باشید و در هرکدام ۱۰۰ پست باشد، این کد تمام ۵۰۰ نوشته‌ی شما را به ترتیب مقدار عددی utid نمایش خواهد داد. <br />
برای محدود کردن نمایش تعداد پست‌ها میتوان از کدهای کنترل کننده حلقه استفاده کرد، مثال:</p>

<pre><code>{{ FOREACH id IN UTIDS }}
   do any thing
   {{ ENTRIES.$id.title }}
   {{ LAST IF loop.count == 10 }}
{{ END }}
بعد از ۱۰ بار تکرار حلقه تمام خواهد شد.
</code></pre>


