{% assign team=site.data.team | where: "team", include.team_name | first %}
{%- assign info = site.data.records | where:"team", include.team_name | group_by:"player" -%}
{%- assign team_match_list = site.data.records | where:"team", include.team_name | group_by:"matchId" -%}

{%- assign team_real_score = 0 %}
{%- assign team_max_score = 0 %}
{% for team_match in team_match_list %}
  {% assign record = team_match.items | first %}
 {% assign score_per_match = record.matchId |minus:1| divided_by: 12 | plus: 1 %}


  {% if record.result == "win" %}
    {% assign team_real_score = team_real_score | plus: score_per_match %}
  {% endif %}
    
  {% assign team_max_score = team_max_score | plus: score_per_match %}

    
{% endfor %}

# {{ include.team_name }} "{{ team.name }}"
---
[回到主页](index.html)

## 基本信息
本页面构建于 {{ site.time }}

- 队长：{{ team.leader }}
- 人数：{{ team.count }}
- 当前积分:{{team_real_score}}
- 丢分：{{team_max_score|minus: team_real_score}}

当前积分

## 出场信息

<table>
 <tr>
    <th>队员</th>
    <th>微信名</th>
    <th>上场</th>
    <th style="text-align:center">英雄</th>
  </tr>

{% for r in info -%}
{%- assign p = site.data.players | where: "player", r.name | first -%}
<tr>
  <td>  {{r.name}}  </td>
  <td>  {{p.wx}}    </td>
  <td style="text-align:right">  {{ r.items | size }}   </td>
  <td>  {% for j in r.items %}  {{j.hero}}  {% endfor %}  </td>
</tr>
{% endfor %}
</table>

## KDA & 参团率

<table>
  <tr>
    <th style="text-align:center">成员</th>
    <th style="text-align:right">KDA</th>
    <th style="text-align:right">参团率</th>
    <th style="text-align:right">场次</th>
    <th style="text-align:right">击杀</th>
    <th style="text-align:right">死亡</th>
    <th style="text-align:right">助攻</th>
    <th style="text-align:right">涉及人头</th>
    <th style="text-align:right">全队人头</th>
  </tr>
{% for r in info -%}
  {%- assign matches = r.items -%}
  {%- assign k = 0 -%}
  {%- assign d = 0 -%}
  {%- assign a = 0 -%}
  {%- assign match_count = 0.0 -%}
  {%- assign team_k = 0 -%}
  {%- for match in matches -%}
      {%- assign k = k | plus: match.K -%}
      {%- assign d = d | plus: match.D -%}
      {%- assign a = a | plus: match.A -%}
      {%- assign team_k = team_k | plus: match.matchK -%}
      {%- assign match_count = match_count | plus: 1 -%}
  {%- endfor -%}  
  {%- assign ka = k | plus: a -%}
<tr> 
  <td> {{ r.name|replace: "Kids.", ""|replace: "Go·", "" |truncate:4,"*"  }} </td>
  <td style="text-align:right"> {{ ka | times: 1.0 | divided_by: d | round: 2 }} </td>
  <td style="text-align:right"> {{ ka | times: 100 | divided_by: team_k | round: 2 }}% </td>
  <td style="text-align:right"> {{ match_count|round }} </td>
  <td style="text-align:right"> {{ k }}  </td>
  <td style="text-align:right"> {{ d }}  </td>
  <td style="text-align:right"> {{ a }} </td> 
  <td style="text-align:right"> {{ ka }} </td> 
  <td style="text-align:right"> {{ team_k }} </td>
</tr>
{% endfor %}
</table>

## 积分贡献率
全队积分:{{team_real_score}}

<table id="tableSort">
 <tr>
    <th>队员</th>
    <th>总贡献率</th>
  <th>拿分效率</th>
  <th>场次</th>
    <th>贡献积分</th>
    <th style="text-align:center">全胜可积</th>
 
  </tr>

{% for r in info -%}
{%- assign player_match_list = r.items %}
{%- assign player_real_score = 0 %}
{%- assign player_max_score = 0 %}
{% for player_match in player_match_list %}
  {% assign score_per_match = player_match.matchId |minus:1| divided_by: 12 | plus: 1 %}

  {% if player_match.result == "win" %}
    {% assign player_real_score = player_real_score | plus: score_per_match %}
  {% endif %}
    
  {% assign player_max_score = player_max_score | plus: score_per_match %}

    
{% endfor %}
<tr>
  <td>  {{r.name}}  </td>
   <td style="text-align:right">  {{player_real_score|times:100|divided_by:team_real_score}}%   </td>
 <td style="text-align:right">  {{player_real_score|times:100|divided_by:player_max_score}}%    </td>
  <td style="text-align:right">  {{player_match_list|size}}    </td>
  <td style="text-align:right">  {{player_real_score}}    </td>
  <td style="text-align:right">  {{player_max_score}}   </td>
 
</tr>
{% endfor %}
</table>


<style type="text/css"> 
th {
    cursor: pointer;
}
</style> 

<script>
const getCellValue = (tr, idx) => tr.children[idx].innerText || tr.children[idx].textContent;

const comparer = (idx, asc) => (a, b) => ((v1, v2) => 
    v1 !== '' && v2 !== '' && !isNaN(v1) && !isNaN(v2) ? v1 - v2 : v1.toString().localeCompare(v2)
    )(getCellValue(asc ? a : b, idx), getCellValue(asc ? b : a, idx));

// do the work...
document.querySelectorAll('th').forEach(th => th.addEventListener('click', (() => {
    const table = th.closest('table');
    Array.from(table.querySelectorAll('tr:nth-child(n+2)'))
        .sort(comparer(Array.from(th.parentNode.children).indexOf(th), this.asc = !this.asc))
        .forEach(tr => table.appendChild(tr) );
})));
</script>
