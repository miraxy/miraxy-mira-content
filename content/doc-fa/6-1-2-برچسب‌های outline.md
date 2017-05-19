---
utid           : 000600010002
title          : برچسب‌های outline
chapter        : 6
chaptername    : قالب
seassion       : 1
seassionname   : دستور زبان
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

<p>تنها دقت داشته باشید برچسب‌های outline حتما باید در اتدای خط باشند و از ساختن فرورفتگی برای آن‌ها خودداری کنید.</p>


