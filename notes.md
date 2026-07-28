---
layout: page
title: Developer Notes
label: Archive
description: Topic-based notes for OS, Network, Cloud, Develop, and related engineering concepts.
permalink: /notes/
---

{% assign grouped_notes = site.notes | group_by: "category" %}

<div class="archive-list">
  {% for group in grouped_notes %}
    <section class="archive-group">
      <h2>{{ group.name }}</h2>
      {% assign docs = group.items | sort: "title" %}
      {% for doc in docs %}
        <a class="list-row" href="{{ doc.url | relative_url }}">
          <span>{{ doc.topic }}</span>
          <strong>{{ doc.title }}</strong>
        </a>
      {% endfor %}
    </section>
  {% endfor %}
</div>
