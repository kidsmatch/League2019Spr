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
    <td>  
来自{{player.team}}的{{player.wx}}在本届比赛共出场{{size}}次,赢了{{ s_win }}场输了{{ s_lose }}场。
        来自{{player.team}}的{{player.wx}}在本届比赛共出场{{size}}次,赢了{{ s_win }}场输了{{ s_lose }}场。
<br>为团队获得{{team_real_score}}分中的{{player_real_score}}分，贡献率{{gongXian}}%,
<br>如果自己上的场次全胜，自己可以拿{{player_max_score}}分，拿分效率{{xiaoLv}}%.
<br>共得到{{s_mvp}}次MVP, 其中{{s_mvp_win}}次胜方MVP,{{s_mvp_lose}}次败方MVP。
<br>共击杀{{k}}次，助攻{{a}}次，合计{{ka}}次。死亡{{d}}次。 KDA值为{{kda}}。参团率为{{canTuan}}%。
<br>平均评分{{avg_score}},其中最高评分{{max_score}},最低评分{{min_score}}。
<br>平均输出{{avg_attack}},最高值{{max_attack}},最低值{{min_attack}}。
<br>平均承伤{{avg_pain}},最高值{{max_pain}},最低值{{min_pain}}。 
    </td>
  </tr>
  {% endfor %}
</table>


本页面构建于 {{ site.time }}
