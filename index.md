---
layout: default
title: sunorry's blog
---
{% include JB/setup %}


## About me

半路 `f2e`

    title : My Blog =)

    author :
      name : sunorry
      email : sunorry@gmail.com
      github : sunorry
      weibo : @大人物大梦想


## Sample Posts

This blog contains sample posts which help stage pages and blog data.
When you don't need the samples anymore just delete the `_posts/core-samples` folder.

    $ rm -rf _posts/core-samples

Here's a sample "posts list".

<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>




