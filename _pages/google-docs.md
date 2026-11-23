---
layout: page
title: Game Project Stories and Scripts
permalink: /story-scripts/
---

These pieces are synced live from Google Docs and update automatically as I revise them.

{% assign grouped_projects = site.categories.google-docs | group_by: "project" %}

{% for group in grouped_projects %}
  <details class="project-dropdown" open>
    <summary class="project-summary">
      {% if group.name != "" %}
        {{ group.name }}
      {% else %}
        Other Game Scripts
      {% endif %}
      <span class="project-count">({{ group.items | size }})</span>
    </summary>

    <ul class="project-post-list">
      {% for post in group.items %}
        <li>
          <span class="post-meta">{{ post.date | date: "%b %-d, %Y" }}</span>
          <h3>
            <a class="post-link" href="{{ post.url | relative_url }}">{{ post.title | escape }}</a>
          </h3>
        </li>
      {% endfor %}
    </ul>
  </details>
{% endfor %}
