# Kids联赛2018 官方主页
## [战绩截图](https://m.weibo.cn/u/6852703787) \| [规则][rule] \| [赞助商][spr]
---

{% assign current = 3 %}
{% assign one = site.data.sponsors | where: "round", current | first %}

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
<!--
|计划日期|时间|比赛双方|
|--------|------|----|
|**11月26日(周一)** | **22:00** | 1队 [荡秋千][t1] <br> 2队[超有趣][t2] |	
|**11月27日(周二)** | **22:00** | 1队 [荡秋千][t1] <br> 3队[全能冠军][t3] |	
|**11月28日(周三)** | **22:00** | 2队 [超有趣][t2] <br> 3队[全能冠军][t3] |	
%}
-->

## 总积分榜

| 队名            | 局数 | 胜局 | 负局 |  积分 |
|-------------   | --: | --: | --: | --: |
| 1队[荡秋千][t1]  | 12  | 8  | 4 | 11 |
| 2队[超有趣][t2]  | 12  | 7  | 5 | 9 |
| 3队[全能冠军][t3]| 12  | 3 | 9 | 4 |

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

本页面构建于 {{ site.time }}

