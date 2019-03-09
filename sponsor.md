赞助商
---
[回到主页](README.md)

## 赞助金额及权益
{% assign list2=site.data.sponsors | sort: "amount" | reverse %} 
{% assign list=site.data.sponsors %} 
<table>
 <tr>
    <th>赞助商</th>
    <th>金额</th>
    <th>姓名</th>
    <th>权益</th>
  </tr>


{% for one in list %}
<tr>
  <td>  {{ one.sponsor }}  </td>
  <td>  {{ one.amount }}    </td>
 <td>  {{ one.name }}    </td>
 
 <td>
 {% if one.flag != "no" %}
    <b>{{one.desp}}</b>
    <font color="red">"{{ one.slogan }}"   </font>
 {% else %}
    <font color="blue">感谢Kids&Go战队所有人的支持！</font>
 {% endif %}
 
 </td>
</tr>
{% endfor %}
</table>

## 赞助费合计
本届共收取赞助2320元。上届遗留286.2元，共计2606.2元。

## 本届费用预算
经所有赞助商同意, 从2606.2元中提取2518.4元用于本届赛事预算, 具体如下。

### 奖金2000元
- 冠军900元。平均每人90元，可购买88.8的皮肤。
- 亚军500元。平均每人50元。
- 其余2队，各300元。平均每人30元，可购买28.8的皮肤。 

### 解说518.4元
- 本届比赛共计9场比赛。小组赛6场 半决赛2 决赛1场
- 每场每个解说员28.8元。即解说一场可以得到一个288皮肤。
- 一场比赛最多2位解说。因此最大预算为 9*2*28.8=518.4元。
- 优先满足未曾解说过的人解说。


