---
layout: page
permalink: /publications/
title: research
description:
nav: true
nav_order: 3
---
what i've published so far and what i'm working on!

{% include bib_search.liquid %}

---

## work in progress

<div class="publications">
  {% bibliography -q @unpublished %}
</div>

---

## publications

<div class="publications">
  {% bibliography -q @article or @incollection %}
</div>
