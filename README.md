# Kids联赛2018 官方主页
### [战绩截图](https://m.weibo.cn/u/6852703787) \| [规则][rule] \| [赞助商][spr] \| [英雄][hero]
---

{% assign current = 5 %}
{% assign one = site.data.sponsors | where: "round", current | first %}
{% assign two = site.data.sponsors | where: "round", "score" | first %}
<table> 
   <tr>    
    <td> 第<b><font color="red">{{ one.round }}</font></b>轮</td>
    <td> 赞助商:<br><font color="red">{{ one.sponsor }} </font></td>
      <td> 
         <b>
            <font color="red">
               <span style="background-color: yellow">{{ one.slogan }}</span>
            </font>
         </b> 
      </td>
   </tr>
</table>


## 赛程预告
本轮已完赛
本届比赛正赛已完赛


## 总积分榜


<table> 
   <tr>   
    <td> 积分榜赞助商:<br><font color="red">{{ two.sponsor }} </font></td>
      <td> 
         <b>
            <font color="red">
               <span style="background-color: yellow">{{ two.slogan }}</span>
            </font>
         </b> 
      </td>
   </tr>
</table>


| 队名            |胜局 | 负局 |  积分 |排名
|-------------   | --: | --: | --: |---|
| 1队<br>[荡秋千][t1]  | 14  | 6 | 27 |<font color="red"> <span style="background-color: yellow">冠军</span>  </font>|
| 2队<br>[超有趣][t2]  |9  | 11 | 14 |亚军|
| 3队<br>[全能冠军][t3]| 7 | 13 | 13 |季军|

## 数据榜

按各队 [1队荡秋千][t1] \| [2队超有趣][t2] \| [3队全能冠军][t3]

按位置 [中路][pos1] \| [上路][pos2] \| [打野][pos3] \| [辅助][pos4] \| [边路射手][pos5] 
(注：非射手职业如果打下路， 视为上路)

[rule]: rule.md
[t1]: team1.md
[t2]: team2.md
[t3]: team3.md
[spr]: sponsor.md
[r0]: round0.md
[r1]: round1.md
[r2]: round2.md
[r3]: round3.md
[r4]: round4.md
[r5]: round5.md
[r6]: round6.md
[hero]: hero.md
[p1]: pos1.md
[p2]: pos2.md
[p3]: pos3.md
[p4]: pos4.md
[p5]: pos5.md


本页面构建于 {{ site.time }}

