{%- assign heros = site.data.records | group_by:"hero" -%}

## 英雄

<table>
  <tr>
    <th style="text-align:center">英雄</th>
    <th style="text-align:right">出场</th>
    <th style="text-align:left">使用者</th>
  </tr>
  
{% for hero in heros -%}
  {%- assign items = hero.items | group_by:"player" -%}
<tr> 
  <td> {{hero.name}} </td>
  <td> {{hero.items|size}} </td>
  <td>
     {% for item in items %}
          {{ item.name }}({{item.items|size}}) 
          胜{{item.items |where:"result","win"|size }}
            
        
           <br>
     {%- endfor -%} 
  </td>
</tr>
{% endfor %}
</table>
