---
layout: page
title: Writing Practice
permalink: /writing-practice/
---

Short creative writing exercises.

<div class="sort-controls">
  <button type="button" class="sort-toggle-btn" onclick="toggleSortOrder(this)" data-direction="asc">
    Sort: Standard (1 → 9) ⇅
  </button>
</div>

{% assign sorted_practice = site.categories.writing-practice | sort: "order" %}
<ul class="post-list sortable-list">
  {% for post in sorted_practice %}
    <li data-order="{{ post.order | default: 9999 }}">
      <span class="post-meta">{{ post.date | date: "%b %-d, %Y" }}</span>
      <h3>
        <a class="post-link" href="{{ post.url | relative_url }}">{{ post.title | escape }}</a>
      </h3>
    </li>
  {% endfor %}
</ul>

<script>
function toggleSortOrder(btn) {
  const isAsc = btn.getAttribute("data-direction") === "asc";
  const nextDir = isAsc ? "desc" : "asc";
  btn.setAttribute("data-direction", nextDir);
  btn.textContent = nextDir === "asc" ? "Sort: Standard (1 → 9) ⇅" : "Sort: Reverse (9 → 1) ⇅";

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
