---
layout: default
title: Home
description: Mathematics research seminar announcements and talks
---
# Applied Analysis Seminar
<p class="lead"><em>Organized by prof. Nikos Yannakakis</em></p>
<p class="lead">
  <a href="https://semfe.ntua.gr/en/">
    Department of Mathematics · School of Applied Mathematical and Physical Sciences · National Technical University of Athens
  </a>
</p>

## About the seminar

This seminar provides a setting for presenting ongoing research, 
studying important results, discussing open problems, and sharing
mathematical techniques across the areas of Applied Analysis, 
Nonlinear Analysis, Partial Differential Equations and 
Calculus of Variations.


## Upcoming Talk

{% assign upcoming_talks = site.talks | where_exp: "talk", "talk.date >= site.time" | sort: "date" %}

{% for talk in upcoming_talks limit:1 %}
<div class="talk-card">


<h3><a href="{{ talk.url | relative_url }}">{{ talk.title }}</a></h3>

<p><strong>Date:</strong> {{ talk.date | date: "%A, %B %-d, %Y" }}<br>
<strong>Time:</strong> {{ talk.time }}<br>
<strong>Speaker:</strong> {{ talk.speaker }}<br>
<strong>Location:</strong> {{ talk.location }}</p>

<p>{{ talk.abstract }}</p>

</div>
{% else %}
<p>No upcoming talks have been announced yet.</p>
{% endfor %}


<p>See the <a href="{{ '/schedule/' | relative_url }}">complete seminar schedule</a> for all announced talks.</p>

<p><a href="{{ '/bibliography/' | relative_url }}">Browse the bibliography</a></p>
