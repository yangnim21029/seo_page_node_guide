---
layout: default
title: SEO 知識庫
description: "所有 SEO 編輯所需的知識與指南。"
---

{% comment %} 準備資料：抓出所有有標題，且不是當前頁面的頁面 {% endcomment %}
{% assign pages_to_show = site.pages | where_exp: "p", "p.title" | where_exp: "p", "p.url != page.url" %}

<div class="container" style="padding: 2rem 1rem;">
  <div class="columns is-centered">
    <div class="column is-three-quarters-tablet is-two-thirds-desktop is-half-widescreen">
      
      {% comment %} 顯示每個頁面的連結按鈕 {% endcomment %}
      {% for item in pages_to_show %}
        <div class="link-item mb-4">
          <a class="button is-fullwidth is-large has-text-weight-semibold" href="{{ site.baseurl }}{{ item.url }}">
            <span>{{ item.title }}</span>
          </a>
          {% if item.description %}
            <p class="link-description has-text-centered mt-2">{{ item.description }}</p>
          {% endif %}
        </div>
      {% endfor %}

    </div>
  </div>
</div>

<style>
  /* 我們可以將背景設為與 Linktree 類似的漸層色，或保持簡潔 */
  body {
    /* 範例漸層背景 */
    /* background: linear-gradient(45deg, #405de6, #5851db, #833ab4, #c13584, #e1306c, #fd1d1d); */
    background-color: #f0f2f5; /* 或是一個簡單的淺灰色背景 */
  }

  .link-item .button {
    background-color: #ffffff; /* 按鈕背景色 */
    color: #363636;           /* 按鈕文字顏色 */
    border: 1px solid #dbdbdb;
    height: auto; /* 自動高度以容納多行文字 */
    padding-top: 1em;
    padding-bottom: 1em;
    transition: transform 0.2s ease-out, box-shadow 0.2s ease-out;
  }

  .link-item .button:hover {
    transform: scale(1.02);
    box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
  }
  
  .link-description {
    color: #4a4a4a;
    font-size: 0.9em;
  }
</style>
