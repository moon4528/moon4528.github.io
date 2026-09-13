---
layout: page
title: Projects
label: Portfolio Archive
description: 문제, 분석, 실행, 검증의 흐름으로 정리한 프로젝트 상세 기록입니다.
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
