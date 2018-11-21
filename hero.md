{%- assign heros = site.data.records | group_by:"hero" -%}

## 英雄

<table>
  <tr>
    <th style="text-align:center">英雄</th>
    <th style="text-align:right">使用者</th>
  </tr>
  
{% for hero in heros -%}
  {%- assign items = hero.items | group_by:"player" -%}
<tr> 
  <td> {{hero.name}} </td>
  <td>
     {% for item in items %}
          {{ item.name }} {{item.items|size}}
     {%- endfor -%} 
  </td>
</tr>
{% endfor %}
</table>
