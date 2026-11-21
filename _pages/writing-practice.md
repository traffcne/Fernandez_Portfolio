---
layout: page
title: Writing Practice
permalink: /writing-practice/
---

Short creative writing exercises, experiments, and standalone pieces.

<ul>
  {% for post in site.categories.writing-practice %}
    <li>
      <span class="post-meta">{{ post.date | date: "%b %-d, %Y" }}</span>
      <h3>
        <a class="post-link" href="{{ post.url | relative_url }}">{{ post.title | escape }}</a>
      </h3>
    </li>
  {% endfor %}
</ul>
