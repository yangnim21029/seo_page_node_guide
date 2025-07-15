---
layout: default
title: SEO 編輯模板
description: 各種編輯所需的 SEO 知識彙整
---

<div class="container">
  {% for page in site.pages %}
    {% if page.url != "/index.html" and page.title %}
      <div class="box">
        <article class="media">
          <div class="media-content">
            <div class="content">
              <p>
                <strong><a href="{{ site.baseurl }}{{ page.url }}" class="is-size-4 has-text-link">{{ page.title }}</a></strong>
                <br>
                <span class="is-size-6 has-text-grey">{{ page.description }}</span>
              </p>
            </div>
            <nav class="level is-mobile">
              <div class="level-left">
                <a href="{{ site.baseurl }}{{ page.url }}" class="button is-success is-outlined is-small">
                  <span>閱讀內容</span>
                  <span class="icon is-small">
                    <i class="fas fa-arrow-right"></i> </span>
                </a>
              </div>
            </nav>
          </div>
        </article>
      </div>
    {% endif %}
  {% endfor %}
</div>
