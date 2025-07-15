---
layout: default
title: SEO 知識庫
description: "所有 SEO 編輯所需的知識與指南。"
---

{% assign pages_to_show = site.pages | where_exp: "p", "p.title" | where_exp: "p", "p.url != page.url" %}

<div class="container" style="padding: 2rem 1rem;">
  <div class="columns is-centered">
    <div class="column is-three-quarters-tablet is-two-thirds-desktop is-half-widescreen">
      
      {% for item in pages_to_show %}
        <div class="mb-4">
          <a class="button is-fullwidth is-large has-text-weight-semibold" href="{{ site.baseurl }}{{ item.url }}">
            <span>{{ item.title }}</span>
          </a>
        </div>
      {% endfor %}

    </div>
  </div>
</div>

<style>
  body {
    background-color: #f0f2f5; /* 簡潔的淺灰色背景 */
  }

  .button {
    background-color: #ffffff;
    color: #363636;
    border: 1px solid #dbdbdb;
    height: auto;
    padding-top: 1em;
    padding-bottom: 1em;
    transition: transform 0.2s ease-out, box-shadow 0.2s ease-out;
  }

  .button:hover {
    transform: scale(1.02);
    box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
  }
</style>
