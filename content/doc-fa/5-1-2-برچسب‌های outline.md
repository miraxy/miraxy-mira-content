---
utid          : 000500010002
title         : برچسب‌های outline
seassion      : 5
seassionname  : قالب
chapter       : 1
chaptername   : دستور زبان
---


<p>همچنین می‌توان این دستورها را با استفاده از برچسب‌های outline نیز نوشت، outline tag ها به شکل پیش فرض %% هستند</p>

<p>مثلا به جای</p>

<pre><code>{{ IF some.list.size -}}
  &lt;ul&gt;
  {{ FOREACH item IN some.list -}}
    &lt;li&gt;{{ item.html }}&lt;/li&gt;
  {{ END -}}
  &lt;/ul&gt;
{{ END -}}
</code></pre>

<p>می‌توان نوشت:</p>

<pre><code>%% IF some.list.size
  &lt;ul&gt;
%%   FOREACH item IN some.list
    &lt;li&gt;{{ item.html }}&lt;/li&gt;
%%   END
  &lt;/ul&gt;
%% END
</code></pre>

<p>تنها دقت داشته باشید برچسب‌های outline حتما باید در ابتدای خط باشند و از ساختن فرورفتگی برای آن‌ها خودداری کنید.</p>


