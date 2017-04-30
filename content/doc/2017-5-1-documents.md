---
utid: 20170501022606
date: 2017-05-01 02:26:06
title: documents
---
## config files

   - title

   - description

   - url

   - root

   - static

   - imageurl

   - publishDIR

     default is 'public'

   - post_num

     number or 'all'

   - archive_post_num

     number or 'all'

   - feed_post_num

     number or 'all'

   - post_sort

     can set 'reverse'

   - default_floor

   - permalink

     /:year/:month/:day/:FIELD_NAME/every_thing_else/:title .html or .php or .xhtnl or any extension you like

   - default_markup

     - markdown -or- md
     - githubmarkdown -or- github -or- ghmd
     - bbcode
     - textile
     - text -or- txt   just add \<br> in enlines
     - html

   - default_extension

     default extension for new content files, default is md

   - output_extension

     default extension for output files, default is html

   - time_zone

   - t_start_tag

     template tag for use in theme, default is {{

   - t_end_tag

     template tag for use in theme, default is }}

   - t_outline_tag

## post

   1. ### header
      - utid

         master key of posts, dont edit it

      - date

      - title

      - _index

         change value for :title, if empty, title will be used for output name

      - _permalink

         change default permalink just for this post

      - _type

         default is post, but can set 'page'

      - _markup

         change body markup language just for this post

      - selective personal fields
         like categories, tags, keywords, author and ...

   2. ### body

      post content body 

## template

   1. ### variables

      1. #### general variables
         - MainTITLE

         - MainDESCRIPTION

         - MainURL

         - MainROOT

         - MainSTATIC

         - MainIMAGEURL

         - MainAUTHOR

         - MainEMAIL

         - ///////////////

         - TITLE

         - DESCRIPTION

         - URL

         - ROOT

         - STATIC

         - IMAGEURL

         - AUTHOR

         - EMAIL

         - ///////////////

         - MAIN : config.yml variables

         - SITE : /config/FLOORNAME.yml

         - ///////////////

         - PageTITLE

         - ///////////////

         - ENTRIES

            all entries in content folder

         - FLOORS

            all FLOORS in content folder, with config.yml(post_number) posts

            ```
            {{ FOREACH site IN FLOORS.values.sort('name') }}

               {{ IF site.SITE.direction == 'right' }}
            		<div dir="rtl">
               {{ ELSE }}
            		<div dir="ltr">
               {{ END }}
               
               <a href="{{ site.root }}">{{ site.name }}</a>
               <p>{{ site.description }}</p>
               
               {{ FOREACH post IN site.posts }}
            		<a href="{{ post.url }}">{{ post.title }}</a>
            		<p>{{ post.body.less }}</p>
               {{ END }}

            {{ END }}
            ```

            ​

            - description
            - name
            - root
            - url
            - SITE : config file variables
            - posts
              - all POSTS loop fields is valid

         - ARCHIVES

            ```
            {{ FOREACH archive IN ARCHIVES.pairs }}
               {{ archive.key }}
               {{ FOREACH item IN archive.value.values.sort('name').sort('number') }}
                  {{ item.name }}
                  {{ item.url }}
                  {{ item.posts.size }}
                  {{ FOREACH utid IN item.posts }}
                     {{ ENTRIES.$utid.url }}
                     {{ ENTRIES.$utid.title }}
                  {{ END }}
               {{ END }}
            {{ END }}
            ```

            ​

            - name
            - url
            - furl
            - posts
            - **if header fields**
               - showname : namespace name
            - **if date archive**
               - number

               - year

               - month

               - month_name

               - number : YearMonth->201705

         - BUILD

            - BUILD.date
            - BUILD.year
            - BUILD.month
            - BUILD.month_name
            - BUILD.month_abbr
            - BUILD.day
            - BUILD.day_name
            - BUILD.day_abbr
            - BUILD.hour
            - BUILD.minute
            - BUILD.second

         - ///////////////

         - POSTS

            is not valid in main.tt2

            ```
            {{ FOREACH post IN POSTS }}
               <a href="{{ post.url }}">{{ post.title }}</a>
               {{ post.CALENDAR.day_name }}
               {{ post.CALENDAR.day }}{{ post.CALENDAR.month_name }}{{ post.CALENDAR.year }}
               {{ IF post.image }}<img src="{{ post.image }}">{{ END }}
               {{ post.body.more }}
               
               {{ IF post.category }}
               {{ FOREACH cat IN post.category }}
                  <a href="{{ cat.url }}">{{ cat.name }}</a>{{ END }}<br>
               {{ END }}

            {{ END }}
            ```

            ​

            - post.utid
            - post.title
            - post.slug
            - **post.url**  : /floor_name/permalink/
            - **post.furl** : your_url.com/floor_name/permalink/
            - post.date
            - post.CALENDAR.year
            - post.CALENDAR.month
            - post.CALENDAR.month_name
            - post.CALENDAR.month_abbr
            - post.CALENDAR.day
            - post.CALENDAR.day_name
            - post.CALENDAR.day_abbr
            - post.CALENDAR.hour
            - post.CALENDAR.minute
            - post.CALENDAR.second
            - **post.body.less** : abstract post
            - **post.body.more** : full post
            - post.($archive_list)

               ``` 
               for example, if tags is a archive field in post's header

               {{ FOREACH tag IN post.tags }}
                  <a href="{{ tag.url }}">{{ tag.name }}</a>
               {{ END }}
               ```

               - name
               - showname (if have namespace)
               - url
               - furl

         - ($listname)_ARCHIVE

            ```
            if category is a archive list

            {{ FOREACH cat IN CATEGORY_ARCHIVE }}

               <a href="{{ cat.url }}">{{ cat.name }}</a> - {{ cat.posts.size }}

               {{ FOREACH utid IN cat.posts }}
                  {{ ENTRIES.$utid.url }}
                  {{ ENTRIES.$utid.title }}
               {{ END }}

            {{ END }}
            ```

            ​

         - ($date)_ARCHIVE

            ```
            {{ FOREACH date IN DATE_ARCHIVE }}

               like $listname_ARCHIVES
               
            {{ END }}
            ```

            ​

         - PAGE
            - PAGE.number
            - PAGE.total
            - PAGE.next.url
            - PAGE.next.title
            - PAGE.prev.url
            - PAGE.prev.title
      2. #### templates variables
         1. main.tt2
            - IS_MAIN

            - UTIDS : all posts's utid field

              ```
              {{ FOREACH utid IN UTIDS }}
                 {{ ENTRIES.$utid.url }}
                 {{ ENTRIES.$utid.title }}
                 
                 all variables in POSTS is valid
                 
              {{ END }}}
              ```

              ​

         2. index.tt2

            - IS_INDEX

         3. archive.tt2

            - ArchiveTITLE

            - ARCH

              - ARCH.name

              - ARCH.url

              - ARCH.furl

              - ARCH.posts

                ```
                {{ FOREACH utid IN ARCH.posts }}
                      {{ ENTRIES.$utid.url }}
                      {{ ENTRIES.$utid.title }}
                {{ END }}
                ```

              - **if field archive**

                - ARCH.showname  (if namespca)

              - **if date archive**

                - ARCH.year
                - ARCH.month
                - ARCH.month_name
                - ARCH.number : YearMonth -> 201608

            - **if field archive**

              - IS_ARCHIVE

            - **if date archive**

              - IS_DATE_ARCHIVE

         4. post.tt2

            - Post_TITLE
            - IS_POST
            - IS_PAGE, if _type: page



