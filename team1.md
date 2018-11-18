# 1队"荡秋千"
---

[回到主页](README.md)

## 基本信息
{{ site.time | in_time_zone:"Beijing"}}

- 队长：Kids.烧酒
- 人数：10人

## 出场信息

|微信名   |   游戏昵称   | 上场 | 英雄 |
|--------|-------------|---:|:------:|
|syuan   | Kids.战神    | 4 | 孙策(2) 娜可露露(2)  |
|先荣    | Kids.剑来    | 4 | 赵云(1) 典韦(2) 张飞(1) |
|fenger  | Kids.Madcat | 3 |白起(3)   |
|高亮    | Kids.嬴荡    | 4|武则天(3) 安琪拉(1) |
|狂奔... |Kids.狂奔     | 2|伽罗(1) 黄忠(1)  |
|teki    | Kids.烧酒    | 1 |狄仁杰(1)|
|陶子    | Kids.半剑    | 1| 牛魔(1)|
|Marin   | Kids.1次就好 | 1 |孙尚香(1)|
|乃鑑    | Kids.烟雨    | 0||
|飞虎    | Kids.王者虎    | 0 ||

# haha

{% assign info = site.data.records | where:"team","1队" | group_by:"player" %}
{{ "|队员|上场次数|英雄|" -}}
{{ "|---|---|---| -}}
{% for r in info %}
  {{r.name}}  |  {{ r.items | size }} |  {% for j in r.items %}  {{j.hero}}  {% endfor %}  {{ "|" -}}
{% endfor %}

# orin
{{ site.data.records | where:"team","1队" | group_by:"player" }}


# wiwi


{% for r in site.data.records %}
     {{ r.player }} {{ r.hero }}
{% endfor %}

