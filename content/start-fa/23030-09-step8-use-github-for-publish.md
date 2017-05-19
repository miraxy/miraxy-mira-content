---
utid: 23030
date: 2017-04-04 01:55:23
title: استفاده از گیت‌هاب برای انتشار
_index: use github for publish
chapter: 09
chaptername: گام هشتم: انتشار
---
هدف در این بخش از راهنما شرح دادن چگونگی منتشر کردن سایتی که با میرا ساخته‌اید بر روی گیت هاب است. برای بهتر متوجه شدن این قسمت نیاز به یک آشنایی حداقلی با گیت‌هاب و چگونگی ساختن مخازن جدید در آن و دانستن مفاهیم و تفاوت‌های مخزن (repository یا repo) با شاخه یا انشعاب یا همان branch دارید.

برای آشنایی بیشتر با صفحات گیتهاب میتوانید مستندات آنرا در این لینک بخوانید:
[User, Organization, and Project Pages](https://help.github.com/articles/user-organization-and-project-pages/)


گیت‌هاب برای استفاده از سرویس pages، راه‌های متفاوتی ارائه می‌کند.

۱- استفاده از دایرکتوری docs در branch master

۲- استفاده از branch فرعی با نام gh-pages

۳- انتشار محتوای ذخیره شده در master

در زیر به شکل کلی در مورد این سه روش می‌خوانیم و در ادامه برای استفاده از هرکدام به شکل اختصاصی برای استفاده در میرا یک راه حل و مثال را پیاده می‌کنیم.

# انتشار با استفاده از دایرکتوری /docs در شاخه‌ی master

بر اساس [راهنمای صفحات گیت هاب](https://help.github.com/articles/configuring-a-publishing-source-for-github-pages/#publishing-your-github-pages-site-from-a-docs-folder-on-your-master-branch)، در صفحات گیت‌هاب با استفاده از docs می‌توان دست به انتشار محتوا زد، راه حل داشتن یک دایرکتوری به نام docs در شاخه‌ی master هر مخزن است.

اگر خواستید از این روش استفاده کنید، باید دایرکتوری public را به docs تغییر نام دهید. برای این‌که هربار که سایت‌تان را با کمک میرا می‌سازید، نیاز به تغییر نام شاخه public نداشته باشید، تنها کافی است در config.yml این خط را اضافه کنید:

	publishDIR: docs

از این به بعد، پس از هر باز اجرا کردن mira build، به جای public، میرا خروجی تولید شده را در دایرکتوری docs ذخیره می‌کند.

شاخه‌ی master را push کنید به مخزن remote و در قسمت setting پروژه در گیت هاب، مشخص کنید که از دایرکتوری docs برای انتشار صفحات استفاده می‌کنید:

	Settings -> GitHub Pages -> Source -> Select master branch /docs folder

دایرکتوری که mira را در آن پیکربندی کردید را کلا به عنوان شاخه‌ی master از مخزن اصلی تعریف کنید و مخزنی که روی گیت‌هاب برای آن ساخته‌اید را به عنوان remote به گیت معرفی کنید.

	git init
	git remote add origin git@github.com:USER/YOUR-SITE-mira.git
	git add --all
	git commit -m 'start'
	git push origin master

از این به بعد، پس از هر بار اجرا کردن mira build و ساخته شدن سایتتان، تغییرات را به گیت اضافه و publish کنید.

	mira build
	git add --all
	git commit -m 'add new content and publish'
	git push origin master

از حالا به بعد اگر آدرس مخزنی که روی گیت هاب ساخته بودید چیزی شبیه به این آدرس بود:

	github.com/USER/YOUR-SITE-mira.git

محتوای شما در آدرسی شبیه به این آدرس با استفاده از فایل‌های قرار گرفته در دایرکتوری docs منتشر خواهد شد:

	USER.github.io/YOUR-SITE-mira

و اگر می‌خواهید از نام دامین اختصاصی خودتان برای نمایش محتوا استفاده کنید، فایلی به نام CNAME را در docs بسازید و نام دامنه‌ی خودتان را در آن بنویسید

	echo YOUR_DOMAIN_NAME.com > CNAME


# انتشار به وسیله‌ی شاخه‌ی gh-pages

راه دیگر انتشار محتوا به وسیله‌ی یک شاخه‌ی جدا به نام gh-pages در مخزن گیت است. آماده سازی آن نسبت به استفاده از شاخه‌ی docs پیچیده‌تر است، اما در مقابل مزایای بیشتری هم دارد.

 - محتوای خام و تنظیمات در شاخه‌ای جدا از خروجی قابل انتشار نگهداری می‌شوند.
 - تاریحچه منبع محتوا و صفحات منتشر شده کاملا جدا از هم نگهداری می‌شود.
 - از دایرکتوری public به شکل پیش‌فرض استفاده می‌کنیم.
 - برای تنظیم کردن پیکربندی انعطاف بیشتری داریم.
 - و...

**توجه کنید**: اگر چندان با گیت آشنا نیستید و دقیقا می‌خواهید قدم به قدم با مثال‌های گیت این راهنما پیش بروید، مخازنی را که در گیت‌هاب می‌سازید، کاملا خالی باشند، هنگام ساختن مخزن در گیت‌هاب، اجازه ساخته شدن فایل README یا gitignore و... را ندهید.

**آماده سازی**:

توضیح: این قسمت را تنها نیاز داریم یک بار انجام دهیم، در طول توضیحات فرض این است که نام remote که استفاده میکنیم origin است، اگر از نام دیگری استفاده میکنید، آن‌ را با origin جایگزین کنید.

قبل از شروع هرکاری، دایرکتوری public را پاک می‌کنیم.

	rm -rf public

یا اگر در ویندوز باشیم

	rd public /s /q

اول گیت را پیکربندی می‌کنیم و دایرکتوری public را به gitignore اضافه میکنیم:

	git init
	echo "public" > .gitignore
	git add --all
	git commit -m 'start'

آدرس مخزنی که در گیت‌هاب ساخته‌اید را به عنوان remote به پروژه اضافه می‌کنیم و شاخه‌ی master را push می‌کنیم.

	git remote add origin git@github.com:USER/YOUR-SITE-mira.git
	git push origin master


سپس شاخه‌ی gh-pages را می‌سازیم و به شکل خالی مقداردهی می‌کنیم و به مخزن remote هم آن‌را اضافه میکنیم.

	git checkout --orphan gh-pages
	git reset --hard
	git commit --allow-empty -m "Initializing gh-pages"
	git push origin gh-pages

به شاخه‌ی master بر می‌گردیم

	git checkout master

و دایرکتوری public را به عنوان worktree برای شاخه‌ی gh-pages مشخص می‌کنیم.(دقت کنید که دایرکتوری public را پاک کرده باشید و هنگام اجرای این دستور وجود نداشته باشد)

	git worktree add -B gh-pages public origin/gh-pages

**انتشار**:

اگر همه مراحل بالا بدون اشکال پیش رفته باشد، حالا همه چیز آماده است. از این به بعد بعد از هر بار اضافه کردن محتوا یک بار مخزن را به روز کنید و بعد از هر build کردن سایت هم یک بار دیگر. ترتیب دستورها چیزی شبیه به این خواهد بود:

	mira new -t 'post title' -f blog
	ویرایش و تولید محتوا و قرار دادن عکس یا سایر ضمیمه‌ها در شاخه استاتیک
	mira build
	git add .
	git commit -m 'add content'
	cd public
	git add .
	git commit -m 'publish'
	cd ..
	به روز کردن مخزن گیت‌هاب پروژه
	git push origin master gh-pages

از حالا به بعد اگر آدرس مخزنی که روی گیت هاب ساخته بودید چیزی شبیه به این آدرس بود:

	github.com/USER/YOUR-SITE-mira.git

محتوای شما در آدرسی شبیه به این آدرس با استفاده از فایل‌های قرار گرفته در دایرکتوری public منتشر خواهد شد:

	USER.github.io/YOUR-SITE-mira

و اگر می‌خواهید از نام دامین اختصاصی خودتان برای نمایش محتوا استفاده کنید، فایلی به نام CNAME را در public بسازید و نام دامنه‌ی خودتان را در آن بنویسید

	echo YOUR_DOMAIN_NAME.com > CNAME

## استفاده از یک اسکریپت:

برای اتومامتیک انجام شدن تمام مراحل بالا، این اسکریپت را دانلود کنید.

[اسکریپت gh-pages.pl](https://raw.githubusercontent.com/kiamazi/mira-tools/master/gh-pages/gh-pages.pl)

حالا یا آن را در دایرکتوری ریشه‌ی میرا کپی کنید، یا در مسیری که در path شما باشد، مثلا دایرکتوری bin در home، و آن را اجرایی کنید
`chmod +x gh-pages.pl`
البته اگر آن را در مسیر میرای خودتان کپی کردید بدون اجرایی کردن آن هم مشکلی نخواهید داشت.

این اسکریپت دو عملکرد دارد، init و push، دقیقا مثل توضیحات بالا که همه چیز را خودمان انجام میدادیم، init را فقط کافی است یک بار اجرا کنید و بعد از آن فقط از push استفاده میکنیم.

اگر آن‌را اجرایی نکرده باشید:

	~/mira$> perl gh-pages.pl --init

و اگر اجرایی شده باشد:

	~/mira$> gh-pages.pl --init

شاخه‌ی gh-pages ساخته شد و دایرکتوری public به عنوان worktree آن معرفی شد.

حالا یک مخزن remote خالی در github می‌سازیم و به پروژه اضافه می‌کنیم:

	git remote add origin git@github.com:USER/REPO_NAME.git

آماده سازی تمام شد، از این به بعد با اجرای دستور زیر:

	~/mira$> perl gh-pages.pl --push
	یا
	~/mira$> gh-pages.pl --push

تمام مراحل add و commit و push به طور خودکار برای هر دو شاخه انجام می‌شود، محتویات تمام دایرکتوری‌های میرا به جز public به شاخه master و محتویات public به شاخه‌ی gh-pages اضافه می‌شوند و دستور push برای هر دو شاخه اجرا می‌شود.

**یک نکته**: اسکریپت فوق یک سوییچ دیگر هم دارد
`--worktree | -w`
اگر زمانی خواستید شاخه‌ی دیگری به جز public به عنوان worktree برای شاخه‌ی gh-pages استفاده شود، میتوانید این سوییچ را هم مورد استفاده قرار دهید.

	~/mira$> perl gh-pages.pl --init -w public/other
	~/mira$> gh-pages.pl --push -w other/path/

اگر مقدار سوییچ worktree با / شروع بشود، اسکریپت اتوماتیک مسیر را در دایرکتوری public در نظر می‌گیرد:

	~/mira$> gh-pages.pl --push --worktree='/path/other'
	برابر است با
	~/mira$> gh-pages.pl --push -w public/path/other

اگر نمی‌خواهید هر سری سوییچ -w را استفاده کنید، اسکریپت را ویرایش کنید و در خط ۱۷ مقدار پیش‌فرض را از public به آدرس مورد نظرتان تغییر دهید:

	worktree => 'public'
	تغییر دهید به
	worktree => 'public/deep/path/'
	یا
	worktree => 'doc'
	worktree => 'another/path'



#انتشار در USER.github.io

در راهنمای صفحات گیت هاب، در کنار ساختن صفحات پروژه، یکی دیگر از راه‌هایی که به آن اشاره شده ساختن صفحات شخصی است. قاعده کلی این صفحات به این صورت است:

 - در آدرسی که با نام کاربری شما در گیت هاب ساخته شده قابل انتشار هستند: USER.github.io
 - محتوا تنها از شاخه‌ی master در مخزنی با نام USER.github.io برای انتشار استفاده می‌شود.

پس برای استفاده از این راه، تنها کافی است دایرکتوری public را به عنوان شاخه master در مخزن USER.github.io معرفی کنید.

ابتدا در گیت هاب مخزنی را با مشخصات اشاره شده بسازید و بعد در دایرکتوری public این کدها را وارد کنید:

	~/mira/public$> git init
	~/mira/public$> git add .
	~/mira/public$> git commit -m 'publish'
	~/mira/public$> git remote add origin git@github.com:USER/USER.github.io.git
	~/mira/public$> git push origin master

## تکمیل

البته یک ایراد وجود دارد، در این حالت فایل‌های محتویات و تنظیمات و تاریخچه آن‌ها و... را در هیچ مخزنی نداریم. برای حل این مشکل از یک راه حل دیگر استفاده می‌کنیم:

- دایرکتوری public را کاملا پاک کنید `rm -rf public`
- روی گیت هاب مخزنی با نام کاربری خود برای انتشار محتوا بسازید: USER.github.io
- روی گیت هاب مخزنی با نام سایت خود بسازید، مثلا YOUR-SITE-mira
- گیت را در دایرکتوری ریشه‌ای که میرا را در آن استفاده می‌کنید، پیکربندی کنید و مخزن YOUR-SITE-mira-content را به عنوان remote به پروژه اضافه کنید.  

دستورهایی که باید وارد کنید چیزی شبیه به این‌ها خواهد بود:

	~/mira$> git init
	~/mira$> git remote add origin git@github.com:USER/YOUR-SITE-mira-content.git
	~/mira$> git add .
	~/mira$> git commit -m 'start'

در آخر public را به عنوان یک ساب ماژول به این مخزن معرفی میکنیم:


	git submodule add -b master git@github.com:USER/USER.github.io.git public

تمام شد، حالا بعد از هر بار mira build، یک بار در شاخه اصلی و یک بار در شاخه public همه چیز را به گیت اضافه کنید و push کنید

	~/mira$> cd public
	~/mira/public$> git add .
	~/mira/public$> git commit -m 'publish'
	~/mira/public$> git push origin master
	~/mira/public$> cd ..
	~/mira$> git add .
	~/mira$> git commit -m 'add content'
	~/mira$> git push origin master
















