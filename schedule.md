---
layout: default
title: Schedule
permalink: /schedule/
---

# Seminar schedule

All announced meetings are listed below, in chronological order.

{% assign talks = site.talks | sort: "date" %}

{% for talk in talks %}
  <div class="talk-card">
    <p class="eyebrow">{{ talk.date | date: "%A, %B %-d, %Y" }}</p>
    <h3><a href="{{ talk.url | relative_url }}">{{ talk.title }}</a></h3>
    <p class="meta">
      {{ talk.speaker | default: "Speaker to be announced" }}
      {% if talk.time %} · {{ talk.time }}{% endif %}
      {% if talk.location %} · {{ talk.location }}{% endif %}
    </p>
    <p><strong>Description: </strong>{{ talk.abstract | default: talk.excerpt | strip_html | truncate: 250 }}</p>
  </div>
{% endfor %}
