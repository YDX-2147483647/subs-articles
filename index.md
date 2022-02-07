---
layout: default
---

# 推送

展示推送（**subs**cription **articles**）<span style='filter: blur(.5em);'>的垃圾堆</span>。

<details markdown='1'>
<summary><code>site.articles</code></summary>
{% assign articles = site.articles | sort: 'title' %}
{% for article in articles %}
-   [{{ article.title }}]({{ article.url | relative_url }})——{{ article.description }}
{% endfor %}
</details>
