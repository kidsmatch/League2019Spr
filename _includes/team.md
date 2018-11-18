
{% assign team=site.data.team | where: "team", include.team_name | first %}

# {{ include.team_name }} " {{ team.name }} "
---
[回到 主页](index.html)

## 基本信息
本页面是模板页面，构建于 {{ site.time }}

- 队长：{{ team.leader }}
- 人数：{{ team.count }}

## 出场信息(自动生成)

{% assign info = site.data.records | where:"team", include.team_name | group_by:"player" %}
{{ "|队员|上场|英雄|" -}}
{{ "|---|---|---| -}}
{% for r in info %}
  {{r.name}}  |  {{ r.items | size }} |  {% for j in r.items %}  {{j.hero}}  {% endfor %}  {{ "|" -}}
{% endfor %}
