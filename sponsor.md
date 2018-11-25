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
    <font color="blue">待定</font>
 {% endif %}
 
 </td>
</tr>
{% endfor %}
</table>
