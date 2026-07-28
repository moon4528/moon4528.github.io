---
layout: page
title: 프로젝트
label: Archive
description: 프로젝트별 개요, 아키텍처, 작업 기록, 회고를 모아둔 공간입니다.
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
