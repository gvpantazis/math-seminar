---
layout: default
title: Home
description: Mathematics research seminar announcements and talks
---
# Applied Analysis Seminar
<p class="lead"><em>Organized by prof. Nikos Yannakakis</em></p>
<p class="lead">
Department of Mathematics · School of Applied Mathematical and Physical Sciences · National Technical University of Athens
</p>

## About the seminar

This seminar provides a setting for presenting ongoing research, 
studying important results, discussing open problems, and sharing
mathematical techniques across the areas of Applied Analysis, 
Nonlinear Analysis, Partial Differential Equations and 
Calculus of Variations.


## Upcoming Talk

<div id="upcoming-talk"></div>

<script>
(function () {
  const talks = [
    {% assign sorted_talks = site.talks | sort: "date" %}
    {% for talk in sorted_talks %}
    {
      title: {{ talk.title | jsonify }},
      date: {{ talk.date | date: "%Y-%m-%d" | jsonify }},
      time: {{ talk.time | jsonify }},
      speaker: {{ talk.speaker | jsonify }},
      location: {{ talk.location | jsonify }},
      abstract: {{ talk.abstract | jsonify }},
      url: {{ talk.url | relative_url | jsonify }}
    }{% unless forloop.last %},{% endunless %}
    {% endfor %}
  ];

  const now = new Date();

  // Interpret seminar dates and times in Athens time.
  const upcoming = talks.filter(talk => {
    const start = new Date(
      talk.date + "T" + talk.time + ":00+03:00"
    );
    return start >= now;
  }).sort((a, b) =>
    (a.date + a.time).localeCompare(b.date + b.time)
  )[0];

  const container = document.getElementById("upcoming-talk");

  if (!upcoming) {
    container.textContent = "No upcoming talks have been announced yet.";
    return;
  }

  const date = new Date(upcoming.date + "T12:00:00");
  const formattedDate = date.toLocaleDateString("en-GB", {
    weekday: "long",
    day: "numeric",
    month: "long",
    year: "numeric"
  });

  container.innerHTML = `
    <div class="talk-card">
      <p class="eyebrow">UPCOMING SEMINAR</p>
      <h3><a href="${upcoming.url}">${upcoming.title}</a></h3>
      <p>
        <strong>Date:</strong> ${formattedDate}<br>
        <strong>Time:</strong> ${upcoming.time}<br>
        <strong>Speaker:</strong> ${upcoming.speaker}<br>
        <strong>Location:</strong> ${upcoming.location}
      </p>
      <p>${upcoming.abstract}</p>
      <p><a href="${upcoming.url}">Read more →</a></p>
    </div>`;
})();
</script>

<p>See the <a href="{{ '/schedule/' | relative_url }}">complete seminar schedule</a> for all announced talks.</p>

<p><a href="{{ '/bibliography/' | relative_url }}">Browse the bibliography</a></p>
