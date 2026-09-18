---
layout: page
permalink: /publications/
title: publications
description: Journal articles, preprints, and conference proceedings in reverse chronological order.
nav: true
nav_order: 2
---

<!-- _pages/publications.md -->

<!-- Bibsearch Feature -->

{% include bib_search.liquid %}

<!-- 전체 편수 / 필터 결과 편수 표시 -->
<div id="bibcount" style="margin: -0.25rem 0 1.25rem; font-size: 0.85rem; color: var(--global-text-color-light);"></div>

<script>
  document.addEventListener("DOMContentLoaded", function () {
    var box = document.getElementById("bibcount");
    if (!box) return;
    var input = document.getElementById("bibsearch");
    var update = function () {
      var all = document.querySelectorAll(".bibliography > li");
      var shown = 0;
      for (var i = 0; i < all.length; i++) {
        if (!all[i].classList.contains("unloaded")) shown++;
      }
      var query = input ? input.value.trim() : "";
      box.textContent = query === "" ? all.length + " publications" : shown + " of " + all.length + " publications match";
    };
    var timer = null;
    var schedule = function () { clearTimeout(timer); timer = setTimeout(update, 50); };
    update();
    // bibsearch.js 가 항목에 .unloaded 클래스를 붙였다 떼는 것을 감지해 숫자를 갱신
    var target = document.querySelector(".publications") || document.body;
    new MutationObserver(schedule).observe(target, { subtree: true, attributes: true, attributeFilter: ["class"] });
    if (input) input.addEventListener("input", schedule);
    window.addEventListener("hashchange", schedule);
  });
</script>

<div class="publications">

{% bibliography %}

</div>
