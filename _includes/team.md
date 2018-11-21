{% assign team=site.data.team | where: "team", include.team_name | first %}
{%- assign info = site.data.records | where:"team", include.team_name | group_by:"player" -%}

# {{ include.team_name }} "{{ team.name }}"
---
[回到主页](index.html)

## 基本信息
本页面构建于 {{ site.time }}

- 队长：{{ team.leader }}
- 人数：{{ team.count }}

## 出场信息


|队员|上场|英雄|
|----|----|----|
{% for r in info -%}
| {{r.name}}  |  {{ r.items | size }} |  {% for j in r.items %}  {{j.hero}}  {% endfor %}  |
{% endfor %}


## 核心数据

|成员|场次|人头|死亡|助攻|涉及人头|全队人头|参团率|
|----|----:|----:|----:|----:|----:|----:|----:|
{% for r in info -%}
  {%- assign matches = r.items -%}
  {%- assign k = 0 -%}
  {%- assign d = 0 -%}
  {%- assign a = 0 -%}
  {%- assign match_count = 0.0 -%}
  {%- assign team_k = 0 -%}
  {%- for match in matches -%}
      {%- assign k = k | plus: match.K -%}
      {%- assign d = d | plus: match.D -%}
      {%- assign a = a | plus: match.A -%}
      {%- assign team_k = team_k | plus: match.matchK -%}
      {%- assign match_count = match_count | plus: 1 -%}
  {%- endfor -%}  
  {%- assign ka = k | plus: a -%}
| {{ r.name|replace: "Kids.", ""|replace: "Go·", "" |truncate:4,"*"  }} | {{ match_count|round }} | {{ k }} | {{ d }} | {{ a }} | {{ ka }} | {{ team_k }} | {{ ka | times: 100 | divided_by: team_k | round: 2 }}% | 
{% endfor %}




## KDA

|成员|场次|击杀|助攻|两项合计|死亡|KDA|
|----|----:|----:|----:|----:|----:|----:|----:|
{% for r in info -%}
  {%- assign matches = r.items -%}
  {%- assign k = 0 -%}
  {%- assign d = 0 -%}
  {%- assign a = 0 -%}
  {%- assign match_count = 0.0 -%}
  {%- assign team_k = 0 -%}
  {%- for match in matches -%}
      {%- assign k = k | plus: match.K -%}
      {%- assign d = d | plus: match.D -%}
      {%- assign a = a | plus: match.A -%}
      {%- assign match_count = match_count | plus: 1 -%}
  {%- endfor -%}  
  {%- assign ka = k | plus: a -%}
| {{ r.name|replace: "Kids.", ""|replace: "Go·", "" |truncate:4,"*"  }} | {{ match_count|round }} | {{ k }} | {{ a }} | {{ ka }} | {{ d }} | {{ ka | times: 1.00 | divided_by: d | round: 2 }} | 
{% endfor -%}
