---
layout: default
title: 首頁
---

# 我的網站

<ul>
{% assign pages_by_dir = site.pages | group_by_exp: "page", "page.dir" %}
{% for dir in pages_by_dir %}
  <li>
    <strong>{{ dir.name | replace: "/", "" | default: "根目錄" }}</strong>
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
