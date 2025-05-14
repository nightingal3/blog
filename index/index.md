---
layout: default
title:   "All Posts"
permalink: /archive/
---

<ul class="archive-list">
{% for post in site.posts %}
  <li>
    <a href="{{ post.url | relative_url }}">
      {{ post.date | date: "%b %-d, %Y" }} – {{ post.title }}
    </a>
  </li>
{% endfor %}
</ul>