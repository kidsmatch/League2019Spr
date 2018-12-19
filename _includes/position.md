{% include sort.html %}

{% assign players = site.data.records | where:"pos", include.pos | group_by:"player" %}

# {{ include.pos }} 数据排行榜
---
[回到主页](index.html)  本页面构建于 {{ site.time }}





