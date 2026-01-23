---
layout: article
title: ブログ
lang: ja
---

{% assign posts = site.posts_ja | sort: "date" | reverse %}
<ul>
{% for p in posts %}
  <li><a href="{{ p.url | relative_url }}">{{ p.title }}</a> — {{ p.date | date: "%Y-%m-%d" }}</li>
{% endfor %}
</ul>

