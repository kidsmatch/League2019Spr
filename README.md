## Kids2019春季赛 官方主页
###  [赛程][sche] \| [规则][rule] \| [赞助商][spr] \| [战绩截图](https://m.weibo.cn/u/6852703787)
---

## 最近赛事

{% assign current = "m4" %}
{% assign one = site.data.sponsors | where: "flag", current | first %}
<table> 
   <tr>    
    <td> <b><font color="red">{{ one.desp }}</font></b> </td>
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

|计划日期|时间|比赛双方|
|--------|------|----|
|**3月13日(周三)** | **22:00** | [A队][ta] VS [D队][td] |

- 主播: (来自B及C队) Kids.小天 Kids.小策策

## 总积分榜

| 队名            |胜局 | 负局 |  积分 |排名
|-------------   | --: | --: | --: |---|
| A队[Darling][ta] | 0 | 4 | 0 | 4|
| B队[欢乐颂][tb]  | 2 | 0 | 2 | 2|
| C队[棒棒糖][tc]  | 3 | 1 | 3 | 1|
| D队[Go][td]      | 1 | 1 | 1 | 3|

{% assign two = site.data.sponsors | where: "flag", "score" | first %}
积分榜赞助商:<font color="red"> {{ two.sponsor }} </font>
  <span style="background-color: yellow"> {{ two.slogan }} </span>
            
[rule]: rule.md
[ta]: teama.md
[tb]: teamb.md
[tc]: teamc.md
[td]: teamd.md
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
[sche]: schedule.md

本页面 构建于 {{ site.time }}

