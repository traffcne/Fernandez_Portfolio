---
layout: page
title: Game Project Stories and Scripts
permalink: /story-scripts/
---

These pieces are synced live from Google Docs and update automatically as I revise them.

<div class="sort-controls">
  <button type="button" class="sort-toggle-btn" onclick="toggleSortOrder(this)" data-direction="asc">
    Sort: ⇅
  </button>
</div>

{% assign grouped_projects = site.categories.google-docs | group_by: "project" %}

{% for group in grouped_projects %}
  <details class="project-dropdown">
    <summary class="project-summary">
      {% if group.name != "" %}
        {{ group.name }}
      {% else %}
        Other Game Scripts
      {% endif %}
      <span class="project-count">({{ group.items | size }})</span>
    </summary>

    {% assign sorted_posts = group.items | sort: "order" %}
    <ul class="project-post-list sortable-list">
      {% for post in sorted_posts %}
        <li data-order="{{ post.order | default: 9999 }}">
          <span class="post-meta">{{ post.date | date: "%b %-d, %Y" }}</span>
          <h3>
            <a class="post-link" href="{{ post.url | relative_url }}">{{ post.title | escape }}</a>
          </h3>
        </li>
      {% endfor %}
    </ul>
  </details>
{% endfor %}

<script>
function toggleSortOrder(btn) {
  const isAsc = btn.getAttribute("data-direction") === "asc";
  const nextDir = isAsc ? "desc" : "asc";
  btn.setAttribute("data-direction", nextDir);
  btn.textContent = nextDir === "asc" ? "Sort: Oldest to Newest ⇅" : "Sort: Newest to Oldest ⇅";

  document.querySelectorAll(".sortable-list").forEach(list => {
    const items = Array.from(list.children);
    items.sort((a, b) => {
      const orderA = parseInt(a.getAttribute("data-order"), 10);
      const orderB = parseInt(b.getAttribute("data-order"), 10);
      return nextDir === "asc" ? orderA - orderB : orderB - orderA;
    });
    items.forEach(item => list.appendChild(item));
  });
}
</script>
