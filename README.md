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


| 队名            | 局数 | 胜局 | 负局 |  积分 |排名
|-------------   | --: | --: | --: | --: |---|
| 1队[荡秋千][t1]  | 20  | 14  | 6 | 27 |冠军|
| 2队[超有趣][t2]  | 20 | 9  | 11 | 14 |亚军|
| 3队[全能冠军][t3]| 20  | 7 | 13 | 13 |季军|

## 参考链接

### [1队荡秋千][t1] \| [2队超有趣][t2] \| [3队全能冠军][t3]

[季前赛][r0]\|[第1轮][r1]\|[第2轮][r2]\|[第3轮][r3]\|[第4轮][r4]\|[第5轮][r5]\|[第6轮][r6]

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

本页面构建于 {{ site.time }}

