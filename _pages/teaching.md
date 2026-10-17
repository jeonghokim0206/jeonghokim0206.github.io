---
layout: page
permalink: /teaching/
title: Teaching
description: Courses taught at Kyung Hee University.
nav: true
nav_order: 6
---

<!--
  _pages/teaching.md
  내용은 전부 _data/teaching.yml 에서 가져옵니다.
  과목을 추가하려면 코드를 건드릴 필요 없이 _data/teaching.yml 에
  year / term / title (+ level, code, note) 만 추가하면 됩니다.
  연도별로 자동으로 묶이고, 최신 연도가 맨 위로 자동 정렬됩니다.
-->

<style>
  .teaching-page .year-block {
    display: grid;
    grid-template-columns: 5rem 1fr;
    gap: 1.5rem;
    padding: 1.4rem 0;
    border-top: 1px solid rgba(128, 128, 128, 0.2);
  }
  .teaching-page .year-block:first-child {
    border-top: none;
    padding-top: 0.25rem;
  }
  .teaching-page .year-label {
    font-size: 1.25rem;
    font-weight: 700;
    color: var(--global-theme-color);
    line-height: 1.4;
  }
  .teaching-page .course {
    display: grid;
    grid-template-columns: 4.5rem 1fr;
    gap: 0.75rem;
    padding: 0.35rem 0;
  }
  .teaching-page .course + .course {
    margin-top: 0.4rem;
  }
  .teaching-page .course-term {
    font-size: 0.8rem;
    font-weight: 600;
    letter-spacing: 0.04em;
    text-transform: uppercase;
    color: var(--global-text-color-light);
    padding-top: 0.2rem;
  }
  .teaching-page .course-title {
    font-size: 1.02rem;
    font-weight: 600;
    margin: 0;
  }
  .teaching-page .course-meta {
    font-size: 0.88rem;
    color: var(--global-text-color-light);
    margin: 0.1rem 0 0;
  }
  @media (max-width: 576px) {
    .teaching-page .year-block {
      grid-template-columns: 1fr;
      gap: 0.6rem;
    }
  }
</style>

{% assign teaching_years = site.data.teaching | group_by: "year" | sort: "name" | reverse %}

<div class="teaching-page">
  {% for year in teaching_years %}
    <div class="year-block">
      <div class="year-label">{{ year.name }}</div>
      <div>
        {% for course in year.items %}
          <div class="course">
            <div class="course-term">{{ course.term }}</div>
            <div>
              <p class="course-title">{{ course.title }}</p>
              {% assign meta = "" %}
              {% if course.level and course.level != "" %}{% assign meta = meta | append: " · " | append: course.level %}{% endif %}
              {% if course.code and course.code != "" %}{% assign meta = meta | append: " · " | append: course.code %}{% endif %}
              {% if course.note and course.note != "" %}{% assign meta = meta | append: " · " | append: course.note %}{% endif %}
              {% assign meta = meta | remove_first: " · " %}
              {% if meta != "" %}
                <p class="course-meta">{{ meta }}</p>
              {% endif %}
            </div>
          </div>
        {% endfor %}
      </div>
    </div>
  {% endfor %}
</div>
