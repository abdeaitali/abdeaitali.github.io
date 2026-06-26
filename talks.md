---
layout: page
title: Talks
permalink: /talks/
---

<div class="page-intro">
  <p>Selected conference talks, seminars, and presentation materials. Related papers and reports are listed on the <a href="/publications/">publications page</a>.</p>
</div>

## Recent talks
---

<div class="project-list">
  {% for talk in site.data.talks.featured %}
  <article class="project-list-item">
    <div>
      <h3>{{ talk.title }}</h3>
      <p>
        {{ talk.event }}{% if talk.location %}, {{ talk.location }}{% endif %}
        {% if talk.links %}
          {% for link in talk.links %}
            <a class="talk-link" href="{{ link.url }}">{{ link.label }}</a>
          {% endfor %}
        {% endif %}
      </p>
    </div>
    <p class="project-list-meta">{{ talk.year }}</p>
  </article>
  {% endfor %}
</div>

## Selected presentation materials
---

<div class="project-list">
  {% for talk in site.data.talks.selected %}
  <article class="project-list-item">
    <div>
      <h3>{{ talk.title }}</h3>
      <p>
        {{ talk.event }}{% if talk.location %}, {{ talk.location }}{% endif %}
        {% if talk.links %}
          {% for link in talk.links %}
            <a class="talk-link" href="{{ link.url }}">{{ link.label }}</a>
          {% endfor %}
        {% endif %}
      </p>
    </div>
    <p class="project-list-meta">{{ talk.year }}</p>
  </article>
  {% endfor %}
</div>
