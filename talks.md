---
layout: default
title: Talks
permalink: /talks/
---

# All Talks

Number of talks detected: {{ site.talks.size }}

{% for talk in site.talks %}
- [{{ talk.title }}]({{ talk.url | relative_url }})
{% else %}
No talks found.
{% endfor %}
