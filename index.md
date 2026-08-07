---
layout: default
title: Home
---

<ul class="post-list">
  {% for post in site.posts %}
    <li>
      <a class="post-link" href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a>
      <p class="post-meta">{{ post.date | date: "%b %-d, %Y" }}</p>
    </li>
  {% endfor %}
</ul>
