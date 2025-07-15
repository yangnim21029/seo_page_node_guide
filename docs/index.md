---
layout: default
title: seo_page_node_guide
---

# seo_page_node_guide

這是一份針對旅遊活動／地區 SEO 寫作的內容規範與範例網站。  
本專案用於整理、分享、展示 SEO 友善的旅遊內容撰寫結構與實作範例，並結合 GitHub Pages + Jekyll 方便協作和自動更新。

---

## 目標

- 提供旅遊主題內容的 SEO 寫作步驟與注意事項
- 分享各種常見的內容範例與結構
- 歸檔不同類型與地區內容撰寫指南
- 利用自動化目錄，方便快速瀏覽所有內容

---

## 資料夾結構簡介

- `/docs/`：各類內容範例與撰寫指南（建議把內容頁都放這裡）
- `/assets/`：圖片、CSS 等靜態資源
- 其他目錄：依主題自訂

---

## 如何貢獻

1. 新增內容時，請於 `/docs/` 目錄下建立 Markdown 檔案，於檔案最上方加上：
   ```
   ---
   title: 你的內容標題
   ---
   ```
2. 推薦每篇內容都包含「主題說明」、「撰寫步驟」、「SEO 注意事項」、「內容結構範例」等段落。
3. 推送後，首頁目錄自動更新，無需手動編輯。

---

## 內容目錄

<nav>
  <ul class="nav-list">
  {% assign pages_by_dir = site.pages | group_by_exp: "page", "page.dir" %}
  {% for dir in pages_by_dir %}
    <li>
      <span class="folder-title">{{ dir.name | replace: "/", "" | default: "根目錄" }}</span>
      <ul>
        {% for page in dir.items %}
          {% if page.url != "/index.html" and page.name != "default.html" and page.title %}
            <li>
              <a href="{{ site.baseurl }}{{ page.url }}">{{ page.title }}</a>
            </li>
          {% endif %}
        {% endfor %}
      </ul>
    </li>
  {% endfor %}
  </ul>
</nav>
