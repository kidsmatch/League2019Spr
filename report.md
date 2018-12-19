---
title: "队员报告"
---

{% assign players = site.data.records | group_by:"player" %}

# KidsLeague2018 队员分析报告
### [回到主页](index.html)

<table>
 <tr>
    <th>队员</th>
    <th>报告</th>
 </tr>
 
{%- for player_and_matchs in players -%}
  {% assign player = site.data.players | where: "player", player_and_matchs.name | first %}
  {% assign matchs = player_and_matchs.items %}
  {% assign s_mvp = matchs | where: "mvp", "yes" | size %}
  {% assign s_win = matchs | where: "result", "win" | size %}
  {% assign s_lose = matchs | where: "result", "lose" | size %}
  {% assign s_mvp_win = matchs | where: "mvp", "yes" | where: "result", "win"  | size %}
  {% assign s_mvp_lose = matchs | where: "mvp", "yes" | where: "result", "lose"  | size %}
  {% assign s_score = 0 %}
  {% assign min_score = 100 %}
  {% assign min_attack = 100 %}
  {% assign min_pain = 100 %}
  {% assign max_score = 0 %}
  {% assign  max_attack = 0 %}
  {% assign  max_pain = 0 %}
  {% assign s_attack = 0 %}
  {% assign s_pain = 0 %}
  {% assign size = matchs | size %}
  {% assign k = 0 -%}
  {% assign d = 0 -%}
  {% assign a = 0 -%}
  {% assign match_count = 0.0 %}
  {% assign team_k = 0 -%}  
  {% assign player_real_score = 0 %}
  {% assign player_max_score = 0 %}
  {% for match in matchs %}
    {% assign s_score = s_score | plus: match.score  %}
    {% assign s_attack = s_attack | plus: match.attack %}
    {% assign s_pain = s_pain | plus: match.pain %}
    {% assign k = k | plus: match.K -%}
    {%- assign d = d | plus: match.D -%}
    {%- assign a = a | plus: match.A -%}
    {%- assign team_k = team_k | plus: match.matchK -%}
    {%- assign match_count = match_count | plus: 1 -%}
    {% assign score_per_match = match.matchId |minus:1| divided_by: 12 | plus: 1 %}
    {% if match.score < min_score %}{% assign min_score = match.score %}{% endif %}
    {% if match.attack < min_attack %}{% assign min_attack = match.attack %}{% endif %}
    {% if match.pain < min_pain %}{% assign min_pain = match.pain %}{% endif %}
    {% if match.score > max_score %}{% assign max_score = match.score %}{% endif %}
    {% if match.attack > max_attack %}{% assign max_attack = match.attack %}{% endif %}
    {% if match.pain > max_pain %}{% assign max_pain = match.pain %}{% endif %}
    {% if match.result == "win" %}
      {% assign player_real_score = player_real_score | plus: score_per_match %}
    {% endif %}
    {% assign player_max_score = player_max_score | plus: score_per_match %}
  {% endfor %}  
  {% assign ka = k | plus: a %}
  {% assign kds = ka | times: 1.0 | divided_by: d | round: 2 %}
  {% assign canTuan = ka | times: 100 | divided_by: team_k | round: 2 %}
  <tr>
    <td>  {{player.wx}}  <br>  ({{player.team}}) </td>  
    <td>  haha </td>
  </tr>
{% endfor %}
</table>


本页面构建于 {{ site.time }}
