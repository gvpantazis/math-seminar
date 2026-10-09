---
layout: default
title: Home
description: Mathematics research seminar announcements and talks
---

<p class="eyebrow">Seminar · Research · Discussion</p>

# Mathematics Research Seminar

<p class="lead">
A meeting place for PhD students, postdoctoral researchers,
and faculty working in mathematical analysis and related fields.
</p>

## About the seminar

The seminar provides a setting for presenting ongoing research,
studying important results, discussing open problems, and sharing
mathematical techniques across related areas.

## Upcoming Talks

{% assign today = site.time | date: "%Y-%m-%d" %}
{% assign upcoming_talks = site.talks | where_exp: "talk", "talk.date >= today" | sort: "date" %}

{% for talk in upcoming_talks %}
<div class="talk-card">
  <p class="eyebrow">{{ talk.date | date: "%A, %d %B %Y" }}</p>
  <h3><a href="{{ talk.url | relative_url }}">{{ talk.title }}</a></h3>
  <p class="meta">{{ talk.speaker }} · {{ talk.time }} · {{ talk.location }}</p>
  <p>{{ talk.abstract }}</p>
</div>
{% else %}
<p>No upcoming talks are scheduled.</p>
{% endfor %}

<p><a href="{{ '/schedule/' | relative_url }}">View the complete schedule →</a></p>
