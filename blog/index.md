---
layout: page
title: Blog
description: Sharing what I have learnt about building ML @ scale
permalink: /blog/
---
I have been learning some pretty awesome things while using Aritificial Intelligence @ scale.
This is my way of sharing what I have learnt.
I have attempted to explain all concepts from first principles. If you find anything missing, leave a comment!

<i> Opinions are solely my own and do not reflect those of my institution or affiliation. </i>

<ul>
  {% for post in site.categories.blog %}
  {% if post.type == "post" %}
    <li>
        <span>{{ post.date | date_to_string }}</span> » <a href="{{ post.url }}" title="{{ post.title }}">{{ post.title }}</a>
        <meta name="description" content="{{ post.summary | escape }}">
        <meta name="keywords" content="{{ post.tags | join: ', ' | escape }}"/>
    </li>
  {% endif %}
  {% endfor %}
</ul>
