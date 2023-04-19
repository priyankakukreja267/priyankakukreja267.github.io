---
layout: page
title: Career
description: Professional Growth
permalink: /career/
---
In the last 15 years, I have learned several lessons to grow professionally. My hope is that I can share this wisdom more broadly and help those who are in the same boat that I was several years ago. 

Leave a comment if you would like to know more about a particular topic!

<i> Opinions are solely my own and do not reflect those of my institution or affiliation. </i>

<ul>
  {% for post in site.categories.career %}
  {% if post.type == "post" %}
    <li>
        <span>{{ post.date | date_to_string }}</span> » <a href="{{ post.url }}" title="{{ post.title }}">{{ post.title }}</a>
        <meta name="description" content="{{ post.summary | escape }}">
        <meta name="keywords" content="{{ post.tags | join: ', ' | escape }}"/>
    </li>
  {% endif %}
  {% endfor %}
</ul>
