---
layout: default
title: SEO 編輯模板
description: 露營、活動類內容的撰寫重點與 SEO 結構建議
---

# 內容分類總覽

<div class="card-grid">
{% for page in site.pages %}
  {% if page.dir == "/docs/" and page.url != "/index.html" and page.title %}
    <div class="card">
      <h2 class="card-title">{{ page.title }}</h2>
      <p class="card-desc">{{ page.description }}</p>
      <a class="card-link" href="{{ site.baseurl }}{{ page.url }}">閱讀內容 &raquo;</a>
    </div>
  {% endif %}
{% endfor %}
</div>

<style>
.card-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
  gap: 2em;
  margin-top: 2em;
}
.card {
  background: #fff;
  border-radius: 1em;
  box-shadow: 0 0.1em 0.5em #c0c0c0;
  padding: 2em 1.2em 1.5em 1.2em;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  min-height: 180px;
}
.card-title {
  font-size: 1.2em;
  font-weight: bold;
  margin-bottom: 0.5em;
  color: #258a25;
}
.card-desc {
  flex-grow: 1;
  color: #444;
  font-size: 1em;
  margin-bottom: 1em;
}
.card-link {
  color: #fff;
  background: #48c774;
  padding: 0.4em 1em;
  border-radius: 0.5em;
  text-decoration: none;
  text-align: right;
  font-size: 0.97em;
  transition: background 0.2s;
}
.card-link:hover {
  background: #258a25;
}
</style>
