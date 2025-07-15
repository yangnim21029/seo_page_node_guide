---
layout: default
title: SEO 知識庫
description: "所有 SEO 編輯所需的知識與指南，以 VS Code 風格呈現。"
---

{% comment %} 準備資料：先抓出所有頁面備用 {% endcomment %}
{% assign all_pages = site.pages | where_exp: "p", "p.title" %}

{% comment %} 篩選出所有「檔案夾」 {% endcomment %}
{% assign folders = all_pages | where: "type", "folder" %}

{% comment %} 篩選出所有「頂層檔案」（沒有 parent 屬性的頁面）{% endcomment %}
{% assign top_level_files = all_pages | where: "parent", nil | where_exp: "p", "p.type != 'folder'" | where_exp: "p", "p.url != page.url" %}


<div class="vscode-directory">
  <ul class="file-tree">
    {% comment %} === 第一層：顯示所有檔案夾及其中的檔案 === {% endcomment %}
    {% for folder in folders %}
      <li class="tree-folder is-expandable">
        <div class="folder-title">
          <span class="icon"><i class="fas fa-folder"></i></span>
          <span class="icon-closed"><i class="fas fa-folder"></i></span>
          <span class="icon-open"><i class="fas fa-folder-open"></i></span>
          <span>{{ folder.title }}</span>
        </div>
        <ul class="nested-tree">
          {% comment %} 找出這個檔案夾的子頁面 {% endcomment %}
          {% assign child_pages = all_pages | where: "parent", folder.basename_without_ext %}
          {% for child in child_pages %}
            <li class="tree-file">
              <a href="{{ site.baseurl }}{{ child.url }}">
                <span class="icon"><i class="fas fa-file-alt"></i></span>
                <span>{{ child.title }}</span>
              </a>
            </li>
          {% endfor %}
        </ul>
      </li>
    {% endfor %}

    {% comment %} === 第二層：顯示所有頂層檔案 === {% endcomment %}
    {% for file in top_level_files %}
      <li class="tree-file">
        <a href="{{ site.baseurl }}{{ file.url }}">
          <span class="icon"><i class="fas fa-file-alt"></i></span>
          <span>{{ file.title }}</span>
        </a>
      </li>
    {% endfor %}
  </ul>
</div>

<style>
  .vscode-directory {
    background-color: #1e1e1e;
    color: #d4d4d4;
    padding: 1.5em;
    border-radius: 8px;
    font-family: 'Segoe UI', 'Menlo', 'Consolas', 'Courier New', monospace;
    font-size: 15px;
  }
  .file-tree, .nested-tree {
    list-style: none;
    padding-left: 0;
    margin: 0;
  }
  .nested-tree {
    padding-left: 22px;
    display: none; /* 預設隱藏 */
    border-left: 1px solid #444;
    margin-left: 9px;
  }
  .file-tree li {
    padding: 4px 0;
    position: relative;
  }
  .folder-title, .tree-file a {
    display: flex;
    align-items: center;
    padding: 4px 8px;
    border-radius: 4px;
    text-decoration: none;
    color: #d4d4d4;
    transition: background-color 0.2s ease;
  }
  .folder-title {
    cursor: pointer;
  }
  .folder-title:hover, .tree-file a:hover {
    background-color: #2a2d2e;
  }
  .file-tree .icon {
    width: 20px;
    text-align: center;
    margin-right: 6px;
    color: #c5c5c5;
  }
  /* --- 圖示切換 --- */
  .folder-title .icon-open { display: none; }
  .folder-title.expanded .icon-closed { display: none; }
  .folder-title.expanded .icon-open { display: inline-block; }
  
  /* --- 展開後的樣式 --- */
  .is-expandable.expanded > .nested-tree {
    display: block;
  }
  .folder-title.expanded > span {
    font-weight: bold;
  }
</style>

<script>
document.addEventListener('DOMContentLoaded', function () {
  const folders = document.querySelectorAll('.vscode-directory .is-expandable .folder-title');

  folders.forEach(folder => {
    folder.addEventListener('click', function() {
      // 切換自身的 expanded class
      this.classList.toggle('expanded');
      
      // 找到對應的子樹 (ul) 並切換顯示
      const subtree = this.nextElementSibling;
      if (subtree && subtree.classList.contains('nested-tree')) {
        subtree.style.display = subtree.style.display === 'block' ? 'none' : 'block';
      }
    });
  });
});
</script>
