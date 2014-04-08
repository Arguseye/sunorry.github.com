---
layout: default
title: sunorry's blog
---
{% include JB/setup %}


<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>

-----------------------------------


## About me

半路 `f2e`

    title : My Blog =)

    author :
      name : sunorry
      email : sunorry@gmail.com
      github : sunorry
      weibo : @大人物大梦想
