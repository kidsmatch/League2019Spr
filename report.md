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
    <td>  
来自{{player.team}}的{{player.wx}}在本届比赛共出场{{size}}次,赢了{{ s_win }}场输了{{ s_lose }}场。
<br>为团队获得team_real_score分中的{{player_real_score}}分，贡献率{{player_real_score|times:100|divided_by:team_real_score}}%,
     如果自己上的场次全胜，自己可以拿{{player_max_score}}分，拿分效率{{player_real_score|times:100|divided_by:player_max_score}}%
<br>共得到{{s_mvp}}次MVP, 其中{{s_mvp_win}}次胜方MVP,{{s_mvp_lose}}次败方MVP。
<br>共击杀{{k}}次，助攻{{a}}次，合计{{ka}}次。死亡{{d}}次。 KDA值为{{kda}}。参团率为{{canTuan}}%。
<br>平均评分{{s_score | divided_by: size| round:1}},其中最高评分{{max_score}},最低评分{{min_score}}。
<br>平均输出{{s_attack | divided_by: size | round:1}},最高值{{max_attack}},最低值{{min_attack}}。
<br>平均承伤{{s_pain | divided_by: size | round:1}},最高值{{max_pain}},最低值{{min_pain}}。
 </td>
  </tr>
{% endfor %}
</table>


本页面构建于 {{ site.time }}
