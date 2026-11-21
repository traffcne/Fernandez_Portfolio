---
layout: page
title: Game Project Stories and Scripts
permalink: /story-scripts/
---

These pieces are synced live from Google Docs and update automatically as I revise them.

<ul>
  {% for post in site.categories.google-docs %}
    <li>
      <span class="post-meta">{{ post.date | date: "%b %-d, %Y" }}</span>
      <h3>
        <a class="post-link" href="{{ post.url | relative_url }}">{{ post.title | escape }}</a>
      </h3>
    </li>
  {% endfor %}
</ul>
