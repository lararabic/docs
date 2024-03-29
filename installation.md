# عملية التثبيت

- [التثبيت ](#installation)
    - [متطلبات العمل](#server-requirements)
    - [تثبيت لارفل](#installing-laravel)
    - [الاعدادات](#configuration)
- [اعدادات الويب سيرفر](#web-server-configuration)
    - [ مجلد الاعدادات](#directory-configuration)
    - [Pretty URLs](#pretty-urls)

<a name="installation"></a>
## عملية الثبيت

<a name="server-requirements"></a>
### متطلبات العمل

يتطلب لارفل بعض المتطلبات ليعمل على السيرفر الخاص بك ، هذه المتطلبات تم تجهيزها بالكامل في ما يسمى بال [Laravel Homestead](/docs/{{version}}/homestead)
وهو عبارة عن نظام افتراضي يتم تثبيته على على الجهاز الخاص بك   يقوم باعداد كافة المتطلبات والتفاصيل التي تحتاجها لتطوير تطبيقات لارفل ،  ننصحك ان تسخدمه كبيئة عمل محلية لك 
اما اذا كنت لا تريد استخدامه وتريد ان تعمل على السيرفر الخاص بك فيجب ان تتوفر هذه  المتطلبات التالية في السيرفر الذي تستخدمه  


`
<div class="content-list" markdown="1">

- PHP >= 7.2.0
- BCMath PHP Extension
- Ctype PHP Extension
- JSON PHP Extension
- Mbstring PHP Extension
- OpenSSL PHP Extension
- PDO PHP Extension
- Tokenizer PHP Extension
- XML PHP Extension
</div>
`




<a name="installing-laravel"></a>
### تثبيت اللارفل

يستخدم اللارفل ال
 [Composer](https://getcomposer.org) 
 وهي عبارة عن اداة تستخدم  لتنزيل وادارة  المكتبات والاضافات في لغة البي اتش بي،  في تنزيل وانشاء مشروع لارفل، تأكد  من  ان الاداة  تعمل في جهازك قبل البدء في عملية التثبيت  



#### تثبيت اللارفل بصورة عامة في الجهاز

قم فتح واجهة الاوامر `terminal/cmd` ثم  نفذ الامر التالي 

    composer global require laravel/installer
    
    
 بعد ان يكتمل تنفيذ الامر السابق قم باضافة مسار اللارفل لمتغيرات نظام التشغيل الخاص بك في ما يسمى بال `PATH` 
يمكنك معرفة المسارات التي تمت اضافتها لل `PATH` 
عبر تنفيذ احد الامرين التالين حسب نظام التشغيل الخاص بك 

نظام الوندوز

	echo %PATH%



نظام لينكس/ماك

	echo $PATH



يجب اضافة المسارات التالية بعد ال`PATH` اعتماداً على نظام التشغيل الذي تستخدمه 
(ابحث عن طريقة تعديل متغيرات نظام التشغيل الخاص بك)


نظام وندوز

	%USERPROFILE%\AppData\Roaming\Composer\vendor\bin



نظام لينكس/ماك

	$HOME/.config/composer/vendor/bin




بعد ان تكتمل عملية التثبيت بالكامل ، يمكنك تشغيل الامر `laravel new ` ملحقا باسم المشروع الذي تريد انشاءه لانشاء مشروع لارفل مثل  `laravel new blog ` سيقوم بانشاء مجلد باسم`blog` يحتوي على نسخة من ملفات لارفل 


		laravel new blog


#### استخدام  Create-Project


قد لا تحتاج لتثبيت اللارفل بصورة دائمة في جهازك ، يمكن استخدام الامر التالي لانشاء  نسخة سريعة من اللارفل عبر الامر `create-project`
مع اسم المشروع الذي تريد انشاءه `blog`

    composer create-project --prefer-dist laravel/laravel blog


#### السيرفر المحلي

اذا كانت لغة PHP مثبتة في جهازك ، يمكنك فتح السيرفر المحلي لتشغيل تطبيق اللارفل عبر الامر `serve` والذي هو احد اوامر `artisan` 





قم بفتح مجلد المشروع الذي تم انشاءه ثم استخدم اداة الاوامر لتشغيل الامر التالي 

		php artisan serve
		
ثم قم بفتح المتصفح وضع الرابط التالي `http://localhost:8000`

**جميع اوامر aratisan يتم تنفيزها في المجلد الرئيسي لتطبيق اللارفل**



هنالك مزيد من الخيارات الخاصة بالسيرفر المحلي يمكن الاطلاع عليها  [Homestead](/docs/{{version}}/homestead) و [Valet](/docs/{{version}}/valet).



<a name="configuration"></a>
### الاعدادات

#### مجلد Public


بعد عملية التثبيت، يجب عليك اعداد السيرفر الخاص بك للقيام بتوجيه المسار الرئيسي الى المجلد public ، يحتوي المجلد public على الملف `index.php`  وهو الذي يقوم باستقبال جميع الhttp requests التي تدخل التطبيق.


#### مجلد الاعدادات
جميع الاعدادات الخاصة بتطبيق لارفل توجد داخل المجلد `config`  ،  ستجد مزيدا من التفاصيل حول جميع ملفات الاعدادات داخل مجلد `config`  ، حاول ان تلقي نظرة على هذه الملفات 



#### صلاحيات الجلدات

بعد عملية تثبيت المشروع ، قد تحتاج الى  اضافة بعض الصلاحيات، المجلدات الموجودة داخل المجلد `storage ` ومجلدات `bootstrap/cache` يجب ان تكون قابلة للكتابة بواسطة السيرفر والا فان التطبيق لن يعمل ،اذا كنت تستخدم  [Homestead](/docs/{{version}}/homestead) فان هذه الصلاحيات تم تسجيلها مسبقا.

#### مفتاح التطبيق

الشيئ التالي الذي يجب القيام به بعد تثبيت اللارفل وضع مفتاح للتطبيق كسلسة نصية عشوائية ، اذا كنت قد استخدمت composer في عملية التثبيت فان  مفتاح التطبيق سيكون قد وضع مسبقا لك ، يمكنك استخدام الامر التالي لوضع مفتاح للتطبيق 

		php artisan key:generate
	 

هذا المتاح يجب ان يكون طوله 32 حرف ، ويوضع في ملف اسمه `.env` او اختصار ل `enviroment` والتي تعني بيئة العمل هذا الملف يحتوي  على جميع المتغيرات المهمة في التطبيق ، اذا لم يكن الملف `.env` موجوداً فستحتاج الان الى تحويل  اسم  `.env.example` الي `.env` 
 **اذا لم يتم وضع مفتاح للتطبيق فان كل عمليات التشفير ومتغيرات الجلسات لن تكون آمنة**

#### اعدادات اضافية

تطبيق لارفل لا يحتاج الى المذيد من الاعدادات الضرورية ليعمل ، يمكنك البدء في عملية التطوير مباشرة ، كما يمكنك القاء نظرة على الاعدادات الخاصة بالتطبيق من خلال الملف `config/app.php`  ، فهو يحتوي عدد من الخيارات مثل التوقيت الزمني الخاص بالتطبيق واللغة المستخدمة قد تريد اجراء تعديلات عليها .


يمكن معرفة العديد من الخيارات الخاصة بالاعدادات مثل :

- [cache ](/docs/{{version}}/cache#configuration)
- [قواعد البيانات](/docs/{{version}}/database#configuration)
- [الجلسات](/docs/{{version}}/session#configuration)



<a name="web-server-configuration"></a>
## اعدادات السيرفر

<a name="directory-configuration"></a>
### اعدادات المجلد 


دائما يحب ان يتم وضع تطبيق اللارفل في المجلد الرئيسي للسيرفر الخاص بك ، محاولة تشغيل تطبيق اللارفل في مجلد فرعي قد تعرض ملفات المشروع الخاص بك للزائر .   
وهو ما يشكل مشكلة امنية قد تكشف محتويات لا تريدها ان تظهر للزوار والمستخدمين

<a name="pretty-urls"></a>
### Pretty URLs

#### Apache

اللارفل يحتوي على ملف`public/.htaccess`  وهو الملف الذي يستخدم لتحويل جميع http requests الي ملف  `index.php` 
تاكد من ان اعدادات ال apache الخاصة بك تيتيح اعادة الكتابة على  ملفات .htaccess وهذه الخيار يدعى  `mod_rewite`في اعدادات السيرفر 

اذا لم يعمل ملف `.htaccess` المضمن في نسخة المشروع مع ال`apache` الخاص بك حاول استبدال محتواه بالتالي

    Options +FollowSymLinks -Indexes
    RewriteEngine On

    RewriteCond %{HTTP:Authorization} .
    RewriteRule .* - [E=HTTP_AUTHORIZATION:%{HTTP:Authorization}]

    RewriteCond %{REQUEST_FILENAME} !-d
    RewriteCond %{REQUEST_FILENAME} !-f
    RewriteRule ^ index.php [L]


#### Nginx

اذا كنت تستخدم Nginx قان الكود التالي سيقوم بعملية تحويل جميع الhttp  requests الى `index.php` 

    location / {
        try_files $uri $uri/ /index.php?$query_string;
    }



عند استخدام  [Homestead](/docs/{{version}}/homestead) او [Valet](/docs/{{version}}/valet)
فان اعددات السيرفر تكون معدة مسبقا .



***ملحوظة: كلمة تطبيق تعني المشروع الذي تم انشاءه***


