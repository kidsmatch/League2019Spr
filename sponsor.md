赞助商
---

{% assign list=site.data.sponsors | sort: "amount", "last" %} 



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
  <td>  第{{one.round}}轮 "{{ one.slogon }}"   </td>
</tr>
{% endfor %}
</table>
