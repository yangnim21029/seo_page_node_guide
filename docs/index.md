---
# 告訴 Jekyll 使用我們剛剛建立的 linktree 版面
layout: linktree
# 設定這個頁面本身的標題
title: Hydra Juice - Links
---

{% assign pages_to_show = site.pages | where_exp: "p", "p.title" | where_exp: "p", "p.url != page.url" %}

<main class="links">
  {% for item in pages_to_show %}
    <a href="{{ site.baseurl }}{{ item.url }}" class="link-button">{{ item.title }}</a>
  {% endfor %}
</main>
