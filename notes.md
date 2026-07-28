---
layout: page
title: 개발자 노트
label: Archive
description: OS, Network, Cloud, Develop 등 기술 학습 내용을 주제별로 정리합니다.
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
