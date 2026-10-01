---
layout: page
permalink: /links/
title: links
description: Collaborators, colleagues, and sites worth bookmarking.
nav: true
nav_order: 10
---

<!--
  _pages/links.md
  내용은 전부 _data/links.yml 에서 가져옵니다.
  새 사람/사이트를 추가하려면 코드를 건드릴 필요 없이
  _data/links.yml 에 name / url / description 세 줄만 추가하면 됩니다.
-->

{% for category in site.data.links.categories %}
  <h2>{{ category.name }}</h2>
  <div class="row row-cols-1 row-cols-md-2 g-3 mb-4">
    {% for item in category.items %}
      <div class="col">
        <div class="card h-100">
          <div class="card-body">
            <h5 class="card-title">
              <a href="{{ item.url }}" target="_blank" rel="noopener noreferrer">{{ item.name }}</a>
            </h5>
            {% if item.description %}
              <p class="card-text text-muted">{{ item.description }}</p>
            {% endif %}
          </div>
        </div>
      </div>
    {% endfor %}
  </div>
{% endfor %}
