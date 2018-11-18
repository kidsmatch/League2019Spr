# 1队"荡秋千"
---

[回到主页](README.md)

## 基本信息
本页面构建于 {{ site.time }}

- 队长：Kids.烧酒
- 人数：10人

## 出场信息(自动生成)

{% assign info = site.data.records | where:"team","1队" | group_by:"player" %}
{{ "|队员|上场|英雄|" -}}
{{ "|---|---|---| -}}
{% for r in info %}
  {{r.name}}  |  {{ r.items | size }} |  {% for j in r.items %}  {{j.hero}}  {% endfor %}  {{ "|" -}}
{% endfor %}

# 调试信息如下
{{ site.data.records | where:"team","1队" | group_by:"player" }}




