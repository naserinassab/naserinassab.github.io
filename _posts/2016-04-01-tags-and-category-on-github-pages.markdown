---
layout: post
title: استفاده از برچسب و دسته بندی در جکیل
permalink: tags_category.html
description: برچسب و دسته بندی در صفحات گیت هاپ بدون استفاده از پلاگین
date: 2016-04-01 00:52:48 +04:30
category: programming
tags: [jekyll,Introductory , Training, github]
author_github: shafiei
---

خدمات  گیت هاپ عالی است! و با ادغام جکیل عالی تر می شود!! اما برخی از محدودیت هایی در این سیستم بزرگ وجود دارد:

+ خود هیچ پلاگینی ندارد

+ [پلاگین های در دسترس محدود هستند](https://pages.github.com/versions/)

هیچ پلاگینی برای برچسب گذاری یا دسته بندی در حال حاضر وجود ندارد. در این جا راهنمای کوچکی برای برچسب گذاری و دسته بندی وجود دارد که می توان آن را پیاده سازی کرد.


1- اضافه کردن کدهای زیر در بالای layout post


    {% raw %}
    {% assign post = page %}
    {% if post.tags.size > 0 %}
        {% capture tags_content %}Posted with {% if post.tags.size == 1 %}<i class="fa fa-tag"></i>{% else %}<i class="fa fa-tags"></i>{% endif %}: {% endcapture %}
        {% for post_tag in post.tags %}
            {% for data_tag in site.data.tags %}
                {% if data_tag.slug == post_tag %}
                    {% assign tag = data_tag %}
                {% endif %}
            {% endfor %}
            {% if tag %}
                {% capture tags_content_temp %}{{ tags_content }}<a href="/blog/tag/{{ tag.slug }}/">{{ tag.name }}</a>{% if forloop.last == false %}, {% endif %}{% endcapture %}
                {% assign tags_content = tags_content_temp %}
            {% endif %}
        {% endfor %}
    {% else %}
        {% assign tags_content = '' %}
    {% endif %}
    {% endraw %}



2- قرار دادن کد زیر برای نمایش برچسب ها در هر جایی از صفحه پست لای اوت که برچسب ها نمایش داده شوند(بالا یا پایین

```
    <p id="post-meta">{% raw %}{{ tags_content }}{% endraw %}</p>
```

3- ساختن یک لای اوت با نام blog_by_tag

    <h1>Articles by tag :{{ page.tag }}</h1>
    <div>
        {% if site.tags[page.tag] %}
            {% for post in site.tags[page.tag] %}
                <a href="{{ post.url }}/">{{ post.title }}</a>
            {% endfor %}
        {% else %}
            <p>There are no posts for this tag.</p>
        {% endif %}
    </div>
    
4- نوشتن کد زیر (نام برچسب ها و دسته بندی ) در بالای هر پست 

    ---
    layout: post
    title: How To Use Tags And Categories On GitHub Pages Without Plugins
    category: programming
    tags: [github, github-pages, jekyll]
    ---
    
5- برای هر تگ استفاده شده باید در فایل **data/tags.yml_** برچسب به صورت زیر تعریف شود.

    - slug: github-pages
      name: GitHub Pages
      
6- برای هر تگ استفاده شده در سایت باید یک تمپلیت خالی مانند **blog/tag/github-pages.md**  تعریف شود.

    ---
    layout: blog_by_tag
    tag: github-pages
    permalink: /blog/tag/github-pages/
    ---
    
اطلاعات بیشتر در [این آدرس](http://www.minddust.com/post/tags-and-categories-on-github-pages/)    
