赞助商
---

{% assign list=site.data.sponsors | sort: "amount" | reverse %} 



<table>
 <tr>
    <th>赞助商</th>
    <th>金额</th>
    <th>支付</th>
    <th>权益</th>
  </tr>


{% for one in list %}
<tr>
  <td>  {{ one.sponsor }}  </td>
  <td>  {{ one.amount }}    </td>
 <td>  {{ one.pay }}    </td>
 
 <td>
 {% if one.round != "0" %}
    <b>第{{one.round}}轮</b>
    <font color="red">"{{ one.slogan }}"   </font>
 {% else %}
    <font color="blue">感谢Kids战队所有人的支持！</font>
 {% endif %}
 
 </td>
</tr>
{% endfor %}
</table>

## 收支

- 赞助额合计1551元

- 奖金共计1236元
  - 冠军：888元（每人88.8）
  - 亚军：288元（每人28.8）
  - 季军： 60元（每人 6.0）
  
- 结余 1551-1236=315元
  - 拟用于主播奖励和其它事宜，后续公示。
