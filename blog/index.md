---
layout: default
title: Blog
permalink: /blog/
---

<p class="tab-label tab-label--blog">Blog</p>
<h1>Blog</h1>

<ul class="section-list">
  {% for post in site.posts %}
  <li>
    <span class="meta">{{ post.date | date: "%B %-d, %Y" }}</span>
    <h3><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h3>
    <p>{{ post.excerpt | strip_html | truncatewords: 25 }}</p>
  </li>
  {% endfor %}
</ul>
