{%- assign heros = site.data.records group_by:"hero" -%}

## 英雄

<table>
  <tr>
    <th style="text-align:center">英雄</th>
    <th style="text-align:right">使用者</th>
  </tr>
  
{% for hero in heros -%}
  {%- assign name = hero.name -%}
  {%- assign items = hero.items -%}
<tr> 
  <td> {{name}} </td>
  <td>
     {% for item in items %}
          {{ item.player }}
     {%- endfor -%} 
  </td>
</tr>
{% endfor %}
</table>
