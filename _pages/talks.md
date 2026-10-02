---
layout: page
permalink: /talks/
title: Talks
description: Invited talks and conference presentations.
nav: true
nav_order: 11
---

<!--
  _pages/talks.md
  내용은 전부 _data/talks.yml 에서 가져옵니다.
  새 발표를 추가하려면 코드를 건드릴 필요 없이
  _data/talks.yml 맨 위에 title / venue / date 세 줄(+ 선택 항목)만 추가하면 됩니다.
-->

<style>
  .talks-page .talk-card {
    display: flex;
    gap: 1rem;
    align-items: flex-start;
    border-radius: 16px;
    padding: 1.1rem 1.35rem;
    margin-bottom: 0.85rem;
    background: rgba(128, 128, 128, 0.06);
    box-shadow: 0 1px 2px rgba(0, 0, 0, 0.05), 0 2px 10px rgba(0, 0, 0, 0.04);
  }
  .talks-page .talk-date {
    flex: 0 0 auto;
    min-width: 4.5rem;
    font-size: 0.85rem;
    font-weight: 700;
    color: var(--global-theme-color);
    padding-top: 0.15rem;
  }
  .talks-page .talk-body {
    flex: 1 1 auto;
  }
  .talks-page .talk-title {
    font-size: 1.05rem;
    font-weight: 600;
    margin: 0 0 0.25rem;
  }
  .talks-page .talk-meta {
    font-size: 0.9rem;
    color: var(--global-text-color-light);
    margin: 0;
  }
  .talks-page .talk-slides {
    display: inline-block;
    margin-top: 0.5rem;
    font-size: 0.82rem;
    font-weight: 600;
    color: var(--global-theme-color);
    text-decoration: none;
  }
  .talks-page .talk-slides:hover {
    text-decoration: underline;
  }
</style>

<div class="talks-page">
  {% for talk in site.data.talks %}
    <div class="talk-card">
      <div class="talk-date">{{ talk.date }}</div>
      <div class="talk-body">
        <p class="talk-title">{{ talk.title }}</p>
        <p class="talk-meta">
          {{ talk.venue }}{% if talk.location and talk.location != "" %} &middot; {{ talk.location }}{% endif %}
        </p>
        {% if talk.slides_url and talk.slides_url != "" %}
          <a class="talk-slides" href="{{ talk.slides_url }}" target="_blank" rel="noopener noreferrer">Slides &rarr;</a>
        {% endif %}
      </div>
    </div>
  {% endfor %}
</div>
