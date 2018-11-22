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

<table>
 <tr>
    <th>队员</th>
    <th>微信名</th>
    <th>上场</th>
    <th style="text-align:center">英雄</th>
  </tr>

{% for r in info -%}
{%- assign p = site.data.players | where: "player", r.name | first -%}
<tr>
  <td>  {{r.name}}  </td>
  <td>  {{p.wx}}    </td>
  <td style="text-align:right">  {{ r.items | size }}   </td>
  <td>  {% for j in r.items %}  {{j.hero}}  {% endfor %}  </td>
</tr>
{% endfor %}
</table>

## KDA & 参团率

<table>
  <tr>
    <th style="text-align:center">成员</th>
    <th style="text-align:right">KDA</th>
    <th style="text-align:right">参团率</th>
    <th style="text-align:right">场次</th>
    <th style="text-align:right">击杀</th>
    <th style="text-align:right">死亡</th>
    <th style="text-align:right">助攻</th>
    <th style="text-align:right">涉及人头</th>
    <th style="text-align:right">全队人头</th>
  </tr>
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
<tr> 
  <td> {{ r.name|replace: "Kids.", ""|replace: "Go·", "" |truncate:4,"*"  }} </td>
  <td style="text-align:right"> {{ ka | times: 1.0 | divided_by: d | round: 2 }} </td>
  <td style="text-align:right"> {{ ka | times: 100 | divided_by: team_k | round: 2 }}% </td>
  <td style="text-align:right"> {{ match_count|round }} </td>
  <td style="text-align:right"> {{ k }}  </td>
  <td style="text-align:right"> {{ d }}  </td>
  <td style="text-align:right"> {{ a }} </td> 
  <td style="text-align:right"> {{ ka }} </td> 
  <td style="text-align:right"> {{ team_k }} </td>
</tr>
{% endfor %}
</table>

## 积分贡献率

<table>
 <tr>
    <th>队员</th>
  <th>贡献率</th>
  <th>场次</th>
    <th>贡献积分</th>
    <th style="text-align:center">全胜可积</th>
    <th style="text-align:center">本队实际</th>
  </tr>

{% for r in info -%}
{%- assign player_match_list = r.items %}
{%- assign player_real_score = 0 %}
{%- assign player_max_score = 0 %}
{% for player_match in player_match_list %}
  {% assign score_per_match = player_match.matchId | divided_by: 12 | plus: 1 %}

  {% if player_match.result == "win" %}
    {% assign player_real_score = player_real_score | plus: score_per_match %}
  {% endif %}
    
  {% assign player_max_score = player_max_score | plus: score_per_match %}

    
{% endfor %}
<tr>
  <td>  {{r.name}}  </td>
 <td style="text-align:right">  {{player_real_score|times:100|divided_by:player_max_score}}%    </td>
  <td style="text-align:right">  {{player_match_list|size}}    </td>
  <td style="text-align:right">  {{player_real_score}}    </td>
  <td style="text-align:right">  {{player_max_score}}   </td>
  <td style="text-align:right">  NA   </td>
</tr>
{% endfor %}
</table>



