---
title: 英雄
---


{% include sort.html %}
{%- assign heros = site.data.records | group_by:"hero" -%}

## 英雄出场

<table>
  <tr>
    <th style="text-align:center">英雄</th>
    <th style="text-align:right">出场</th>
     <th style="text-align:right">胜率</th>
    <th style="text-align:left">使用者</th>
  </tr>
  
{% for hero in heros -%}
  {%- assign items = hero.items | group_by:"player" -%}
<tr> 
  <td> {{hero.name}} </td>
  
  {% assign win = hero.items | where:"result","win"|size %}
   {% assign all = | hero.items|size %}
  <td> {{all}}战<br>{{win}}胜 </td>
   <td> {{win|times:100|divided_by:all}}% </td>
  <td>
     {% for item in items %}
          {{ item.name |replace:"Kids.",""|replace:"Go·",""}} {{item.items|size}}
          胜 {{item.items |where:"result","win"|size }}
            
        
           <br>
     {%- endfor -%} 
  </td>
</tr>
{% endfor %}
</table>
