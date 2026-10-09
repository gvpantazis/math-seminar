---
layout: default
title: Archive
permalink: /archive/
---

# Previous meetings

A record of previous seminar presentations.

{% assign talks = site.talks | sort: "date" | reverse %}

{% for talk in talks %}
  {% assign talk_day = talk.date | date: "%Y-%m-%d" %}
  {% assign today = site.time | date: "%Y-%m-%d" %}

  {% if talk_day < today %}
    <div class="talk-card">
      <p class="eyebrow">{{ talk.date | date: "%d %B %Y" }}</p>
      <h3><a href="{{ talk.url | relative_url }}">{{ talk.title }}</a></h3>
      <p class="meta">{{ talk.speaker }}</p>
      <p>{{ talk.abstract | default: talk.excerpt | strip_html | truncate: 250 }}</p>
    </div>
  {% endif %}
{% endfor %}
