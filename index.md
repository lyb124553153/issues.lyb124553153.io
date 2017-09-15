---
layout: default
title: 做点笔记
---
<h2>{{ page.title }}</h2>
<p>历史记录</p>
<ul>
    　　　　{% for post in site.posts %}
    　　<li>{{ post.date | date_to_string }} <a href="{{site.baseurl}}{{post.url}}">{{ post.title }}</a></li>
    　　　　{% endfor %}
</ul>
