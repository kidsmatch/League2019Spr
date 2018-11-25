赞助商
---

{% assign list=site.data.sponsors | sort: "amount", "last" %} 

{% for one in list %}
  {{ one.sponsor }} {{one.amount}} {{ one.slogon }}
{% endfor %}

