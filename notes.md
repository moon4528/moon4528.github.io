---
layout: page
title: Developer Notes
label: Engineering Archive
description: 백엔드 개발에 필요한 OS, Network, Cloud 지식을 질문과 근거 중심으로 정리합니다.
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
