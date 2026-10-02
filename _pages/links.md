---
layout: page
permalink: /links/
title: Links
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

<style>
  .links-page .category-title {
    font-size: 0.8rem;
    font-weight: 700;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    color: var(--global-text-color-light);
    margin: 2.25rem 0 1rem;
  }
  .links-page .category-title:first-of-type {
    margin-top: 0.25rem;
  }
  .links-page .link-card {
    display: block;
    height: 100%;
    border-radius: 16px;
    padding: 1.15rem 1.35rem;
    background: rgba(128, 128, 128, 0.06);
    box-shadow: 0 1px 2px rgba(0, 0, 0, 0.05), 0 2px 10px rgba(0, 0, 0, 0.04);
    transition: transform 0.15s ease, box-shadow 0.15s ease, background 0.15s ease;
    color: inherit;
    text-decoration: none;
  }
  .links-page .link-card:hover {
    transform: translateY(-3px);
    box-shadow: 0 8px 20px rgba(0, 0, 0, 0.10);
    background: rgba(128, 128, 128, 0.1);
  }
  .links-page .link-name {
    font-size: 1.05rem;
    font-weight: 600;
    margin: 0 0 0.3rem;
    color: var(--global-theme-color); /* 사이트 테마의 강조색 변수: 라이트모드=보라, 다크모드=시안으로 자동 전환 */
  }
  .links-page .link-card:hover .link-name {
    text-decoration: underline;
  }
  .links-page .link-desc {
    font-size: 0.9rem;
    color: var(--global-text-color-light);
    margin: 0;
  }
</style>

<div class="links-page">
  {% for category in site.data.links.categories %}
    <h2 class="category-title">{{ category.name }}</h2>
    <div class="row row-cols-1 row-cols-md-2 g-3 mb-5">
      {% for item in category.items %}
        <div class="col">
          <a class="link-card" href="{{ item.url }}" target="_blank" rel="noopener noreferrer">
            <p class="link-name">{{ item.name }}</p>
            {% if item.description %}
              <p class="link-desc">{{ item.description }}</p>
            {% endif %}
          </a>
        </div>
      {% endfor %}
    </div>
  {% endfor %}
</div>
