---
utid           : 000500030020
title          : ARCHIVES
chapter        : 5
chaptername    : پوسته
seassion       : 3
seassionname   : توضیحاتی در مورد برچسب‌ها
---


<p>تمام آرشیوهای موجود در طبقه یا همان سایت</p>

<p>در صورتیکه از یک پوسته یکسان برای چند طبقه که آرشیوهایی با فیلدها و نام‌های متفاوت دارند استفاده میکنید، میتوانید برای نمایش تمام آرشیو‌ها، بدون اهمیت اینکه چه نامی دارند از این برچسب استفاده کنید.</p>

<p>مقدار این برچسب چیزی شبیه به این است:</p>

<pre><code>'categories' =&gt; {
          "CAT1" =&gt; {
                'name' =&gt; "CAT1",
                    'url' =&gt; "/FLOOR/categories/CAT1namespace/",
                    'posts' =&gt; [
                               '20170210173327',
                               '20170210173313',
                               '20170210174503',
                               '20170210172431',
                               '20170210173319'
                             ]
              },
          "CAT2" =&gt; {
                'name' =&gt; "CAT2",
                    'url' =&gt; "/FLOOR/categories/CAT2namespace/",
                    'posts' =&gt; [
                               '20170210173327',
                               '20170210173313',
                               '20170210174503',
                               '20170210172431',
                               '20170210173319'
                             ]
             }
},
'date' =&gt; {
      '201702' =&gt; {
              'year' =&gt; '2017',
              'month' =&gt; '02',
              'url' =&gt; '/fa/archive/2017/02/',
              'name' =&gt; 'February 2017',
              'number' =&gt; '2017 - 02',
              'posts' =&gt; [
                         '20170210173327',
                         '20170210173313',
                         '20170210174503',
                         '20170210172431',
                         '20170210173319'
                       ]
              }
}
</code></pre>

<p>با استفاده از IF میتوانید رفتار متفاوتی را برای هر نوع آرشیو در صورت وجود تعریف کنید</p>

<p>نحوه استفاده:</p>

<pre><code>{{ FOREACH archive IN ARCHIVES.pairs }}
  {{ archive.key }} نام آرشیو
  &lt;hr&gt;
  {{ FOREACH item IN archive.value.values }}
    &lt;a href="{{ item.url }}"&gt;{{ item.name }}&lt;/a&gt;
    {{ IF (archive.key == 'categories') }}&lt;br&gt;{{ END }}
    {{ IF (archive.key == 'date') or (archive.key == 'jdate') }}&lt;br&gt;{{ END }}
    {{ IF (archive.key == 'author') }}&lt;br&gt;{{ END }}
    {{ IF (archive.key == 'tags') }}&amp;nbsp;-&amp;nbsp;{{ END }}
  {{- END }}
  &lt;br&gt;
{{- END }}
</code></pre>


