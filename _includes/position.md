{% include sort.html %}

{% assign players = site.data.records | where:"pos", include.pos | group_by:"player" %}

# {{ include.posDes }} 数据排行榜
---
[回到主页](index.html)  本页面构建于 {{ site.time }}

<table>
 <tr>
    <th>队员</th>
  <th>平均分</th>
    <th>胜</th>
    <th>负</th>
    <th>mvp</th>
  <th>输出</th> 
  <th>承伤</th> 
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
 <td style="text-align:right">  {{s_score | divided_by: size| round:1}} </td>
    <td style="text-align:right">  {{ s_win }}   </td>
    <td style="text-align:right">  {{ s_lose }}   </td>
 <td style="text-align:right">  {{s_mvp}} <br> {{s_mvp_win}}胜 </td>
 <td style="text-align:right">  {{s_attack | divided_by: size | round:1}} </td>
 <td style="text-align:right">  {{s_pain | divided_by: size | round:1}} </td>
  </tr>
{%- endfor -%}
</table>




