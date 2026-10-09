Number of talks: {{ site.talks.size }}
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

## Upcoming talks

{% assign talks = site.talks | sort: "date" %}
{% assign found = false %}

{% for talk in talks %}
  {% assign talk_day = talk.date | date: "%Y-%m-%d" %}
  {% assign today = site.time | date: "%Y-%m-%d" %}

  {% if talk_day >= today %}
    {% assign found = true %}
    <div class="talk-card">
      <p class="eyebrow">{{ talk.date | date: "%A, %d %B %Y" }}</p>
      <h3><a href="{{ talk.url | relative_url }}">{{ talk.title }}</a></h3>
      <p class="meta">
        {% if talk.speaker %}{{ talk.speaker }}{% endif %}
        {% if talk.time %} · {{ talk.time }}{% endif %}
        {% if talk.location %} · {{ talk.location }}{% endif %}
      </p>
      <p>{{ talk.abstract | default: talk.excerpt | strip_html | truncate: 250 }}</p>
    </div>
  {% endif %}
{% endfor %}

{% unless found %}
<p>No upcoming talks have been announced yet.</p>
{% endunless %}

<p><a href="{{ '/schedule/' | relative_url }}">View the complete schedule →</a></p>
