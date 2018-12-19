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
    {% assign s_attack = 0 %}
      {% assign s_pain = 0 %}
      {% assign size = matchs | size %}
  {% for match in matchs %}
    {% assign s_score = s_score | plus: match.score  %}
    {% assign s_attack = s_attack | plus: match.attack %}
    {% assign s_pain = s_pain | plus: match.pain %}
  {% endfor %}
 
 
  <tr>
    <td>  {{player.wx}}  <br>  ({{player.team}}) </td>  
    <td>  来自{{player.team}}的{{player.wx}}在本届比赛共出场{{size}}次,赢了{{ s_win }}场输了{{ s_lose }}场。
共得到{{s_mvp}}次MVP, 其中{{s_mvp_win}}次胜方MVP,{{s_mvp_lose}}次败方MVP。
平均评分{{s_score | divided_by: size| round:1}},其中最高评分{{max_score}},最低评分{{min_score}}。
平均输出{{s_attack | divided_by: size | round:1}},最高值{{max_attack}},最低值{{min_attack}}。
平均承伤{{s_pain | divided_by: size | round:1}},最高值{{max_pain}},最低值{{min_pain}}。

  </tr>
{%- endfor -%}
</table>


本页面构建于 {{ site.time }}
