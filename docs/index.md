---
layout: default
title: SEO 知識庫
description: "所有 SEO 編輯所需的知識與指南。"
---

{% assign pages_to_show = site.pages | where_exp: "p", "p.title" | where_exp: "p", "p.url != page.url" %}

<div class="container" style="padding: 2rem 1rem;">
  <div class="columns is-centered">
    <div class="column is-three-quarters-tablet is-two-thirds-desktop is-half-widescreen has-text-centered">

      <header class="profile-header mb-6">
        <figure class="image is-128x128 is-inline-block">
          <img class="is-rounded" src="{{ site.baseurl }}/assets/images/profile.png" alt="個人頭像">
        </figure>
        <h1 class="title is-2 has-text-white mt-4">理財學伴 Cindy & Shirley</h1>
        <p class="subtitle is-5 has-text-light">歡迎來到 Cindy & Shirley 的理財學習圈</p>
      </header>

      <div class="links-container">
        {% for item in pages_to_show %}
          <div class="mb-4">
            <a class="button is-fullwidth is-large has-text-weight-medium" href="{{ site.baseurl }}{{ item.url }}">
              {% if item.icon %}
              <span class="icon is-medium">
                <i class="{{ item.icon }}"></i>
              </span>
              {% endif %}
              <span>{{ item.title }}</span>
            </a>
          </div>
        {% endfor %}
      </div>

    </div>
  </div>
</div>

<style>
  body {
    /* 深色背景 */
    background-color: #1c222e; 
    
    /* 如果您想用背景圖片，請使用以下樣式並調整圖片路徑 */
    /*
    background-image: linear-gradient(rgba(28, 34, 46, 0.8), rgba(28, 34, 46, 0.95)), url('{{ site.baseurl }}/assets/images/your-background.jpg');
    background-size: cover;
    background-position: center;
    background-attachment: fixed;
    */
  }

  /* 按鈕樣式 */
  .button {
    background-color: rgba(255, 255, 255, 0.1);
    color: #ffffff;
    border: 1px solid rgba(255, 255, 255, 0.2);
    height: auto;
    padding-top: 0.8em;
    padding-bottom: 0.8em;
    transition: background-color 0.2s ease-out;
    justify-content: center; /* 讓圖示和文字水平置中 */
  }

  .button:hover {
    background-color: rgba(255, 255, 255, 0.15);
  }

  .button .icon {
    position: absolute;
    left: 1.5rem; /* 將圖示固定在左側 */
  }
  .button span:last-child {
    flex-grow: 1; /* 讓文字佔據剩餘空間以保持置中 */
  }

</style>
