---
layout: linktree
title: Editor's SEO Guide
description: Topic and Pages Guide
---

{% assign pages_to_show = site.pages | where_exp: "p", "p.title" | where_exp: "p", "p.url != page.url" %}

<main class="links">
  {% for item in pages_to_show %}
    <a href="{{ site.baseurl }}{{ item.url }}" class="link-button">{{ item.title }}</a>
  {% endfor %}
</main>
