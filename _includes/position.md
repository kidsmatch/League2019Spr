{% include sort.html %}

{% assign players = site.data.records | where:"pos", include.pos | group_by:"player" %}

# {{ include.pos }} 数据排行榜
---
[回到主页](index.html)

## 出场信息

<table>
 <tr>
    <th>队员</th>
    <th>胜</th>
    <th>负</th>
    <th>mvp<th> 
  </tr>

{% for player_and_matchs in players %}
  {% assign player = site.data.players | where: "player", player_and_matchs.name | first -%}
  
  {% assign matchs = player_and_matchs.items %}
  {% assign s_mvp = matchs | where: "mvp", "yes" | size %}
  {% assign s_win = matchs | where: "result", "yes" | size %}
  {% assign s_lose = matchs | where: "mvp", "no" | size %}
  
  <tr>
    <td>  {{player.name}} <br> ( {{player.wx}} )  </td>  
    <td style="text-align:right">  {{ s_win }}   </td>
    <td style="text-align:right">  {{ s_lose }}   </td>
    <td style="text-align:right">  {{ s_mvp }}   </td>
  </tr>
{% endfor %}
</table>




