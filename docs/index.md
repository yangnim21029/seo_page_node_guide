---
layout: default
title: SEO 知識庫
description: "所有 SEO 編輯所需的知識與指南。"
---

{% assign pages_to_show = site.pages | where_exp: "p", "p.title" | where_exp: "p", "p.url != page.url" %}

<div class="bg-dark text-white">
  <div class="container min-vh-100 d-flex flex-column justify-content-center py-5">
    <div class="row justify-content-center">
      <div class="col-12 col-md-8 col-lg-6">

        <header class="text-center mb-5">
          <img src="{{ site.baseurl }}/assets/images/profile.png" 
               class="img-fluid rounded-circle mx-auto d-block mb-4" 
               alt="個人頭像" 
               style="max-width: 128px;">
          
          <h1 class="display-5 fw-bold text-light">理財學伴 Cindy & Shirley</h1>
          <p class="lead text-white-50">歡迎來到 Cindy & Shirley 的理財學習圈</p>
        </header>

        <main>
          <div class="d-grid gap-3">

            {% for item in pages_to_show %}
            <a class="btn btn-light btn-lg fw-semibold p-3" href="{{ site.baseurl }}{{ item.url }}" role="button">
              {{ item.title }}
            </a>
            {% endfor %}

          </div>
        </main>

      </div>
    </div>
  </div>
</div>
