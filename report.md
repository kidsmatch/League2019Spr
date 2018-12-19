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
  {% for player_and_matchs in players %}
  {% assign player = site.data.players | where: "player", player_and_matchs.name | first %}
  <tr>
    <td>  {{player.wx}}  <br>  ({{player.team}}) </td>  
    <td>  haha </td>
  </tr>
  {% endfor %}
</table>


本页面构建于 {{ site.time }}
