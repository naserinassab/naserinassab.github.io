---
layout: post
title: اضافه کردن نام نویسنده پست
permalink: author_name_in_jekyll.html
description: Some Description
date: 2016-04-03 22:17:53 +04:30
category: programming
tags: [jekyll,Introductory , Training]
author_github: shafiei
---

این وبلاگ با جکیل طراحی شده است،معمولا در هر وبلاگ نام نویسنده، شناسه گیت هاب، توییتر و تصویر نویسنده در صورت وجود نمایش داده می شود.

در این پست در مورد نمایش اطلاعات نویسنده بحث خواهد شد.

یکی از راه ها ایجاد فایل **authors.yml** در پوشه **data_** که در ریشه اصلی سایت ایجاد کرده ایم، است.

بعد اطلاعات نویسنده را به عنوان مثال مثل زیر در آن وارد می کنیم.



    vipulnsward:
      name: Vipul
      avatar: http://bigbinary.com/assets/team/vipul.jpg
      github: vipulnsward
      twitter: vipulnsward
    neerajdotname:
      name: Neeraj Singh
      avatar: http://bigbinary.com/assets/team/neeraj.jpg
      github: neerajdotname
      twitter: neerajdotname
    


فایل های با پسوند **yml** به طور خودکار پردازش می شوند.

در مرحله بعد باید کد زیر را به ابتدای پست اضافه کنیم.



    ---
    layout: post
    title: How to deploy jekyll site to heroku
    categories: [Ruby]
    author_github: neerajdotname
    ---
    


نکته این است که خط کد معرفی نویسنده باید آخرین خط باشد.

در آخرین مرحله باید در لای اوت پست کد مربوط به نمایش نام نویسنده وارد شود.


    <span class="author-name">
      {{ site.data.authors.[page.author_github].name }}
    </span>



اطلاعات بیشتر در [آدرس](http://blog.bigbinary.com/2015/01/09/author-information-in-jekyll-blog.html)

موفق باشید.
