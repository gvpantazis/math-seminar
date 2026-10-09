---
layout: default
title: Home
description: Mathematics research seminar announcements and talks
---

<p class="eyebrow">Seminar · Research · Discussion</p>

# Applied Analysis and PDEs

<p class="lead">
A meeting place for PhD students, postdoctoral researchers,
and faculty working in mathematical analysis and related fields.
</p>

## About the seminar

The seminar provides a setting for presenting ongoing research,
studying important results, discussing open problems, and sharing
mathematical techniques across related areas.

## Upcoming Talks
{% assign upcoming_talks = site.talks | where_exp: "talk", "talk.date >= site.time" | sort: "date" %}

{% for talk in upcoming_talks limit:1 %}
### [{{ talk.title }}]({{ talk.url | relative_url }})

**Date:** {{ talk.date | date: "%A, %B %-d, %Y" }}  
**Time:** {{ talk.time }}  
**Speaker:** {{ talk.speaker }}  
**Location:** {{ talk.location }}

{{ talk.abstract }}
{% else %}
No upcoming talks have been announced yet.
{% endfor %}
<p>See the <a href="{{ '/schedule/' | relative_url }}">complete seminar schedule</a> for all announced talks.</p>

<p><a href="{{ '/bibliography/' | relative_url }}">Browse the bibliography</a></p>
