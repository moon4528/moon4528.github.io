---
layout: page
title: Projects
label: Archive
description: Project overviews, architecture notes, work logs, and retrospectives.
permalink: /projects/
---

{% assign grouped_projects = site.projects | group_by: "project" %}

<div class="archive-list">
  {% for group in grouped_projects %}
    <section class="archive-group">
      <h2>{{ group.name }}</h2>
      {% assign docs = group.items | sort: "order" %}
      {% for doc in docs %}
        <a class="list-row" href="{{ doc.url | relative_url }}">
          <span>{{ doc.section }}</span>
          <strong>{{ doc.title }}</strong>
        </a>
      {% endfor %}
    </section>
  {% endfor %}
</div>
