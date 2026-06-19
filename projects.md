---
layout: page
title: Projects
permalink: /projects/
---

## Ongoing projects
---

<div class="project-list">
  {% for project in site.data.projects.current %}
  <article class="project-list-item" id="{{ project.id }}">
    <div>
      <h3>
        {% capture project_title %}{% if project.abbreviation %}{{ project.abbreviation }} — {{ project.title }}{% else %}{{ project.title }}{% endif %}{% endcapture %}
        {% if project.url %}<a href="{{ project.url }}">{{ project_title | strip }}</a>{% else %}{{ project_title | strip }}{% endif %}
      </h3>
      <p>{{ project.summary }}</p>
    </div>
    <p class="project-list-meta">
      {{ project.years }}
      {% if project.sponsor %}<span>Funded by {{ project.sponsor }}</span>{% endif %}
    </p>
  </article>
  {% endfor %}
</div>

## Completed projects
---

<div class="project-list">
  {% for project in site.data.projects.completed %}
  <article class="project-list-item" id="{{ project.id }}">
    <div>
      <h3>
        {% capture project_title %}{% if project.abbreviation %}{{ project.abbreviation }} — {{ project.title }}{% else %}{{ project.title }}{% endif %}{% endcapture %}
        {% if project.url %}<a href="{{ project.url }}">{{ project_title | strip }}</a>{% else %}{{ project_title | strip }}{% endif %}
      </h3>
      <p>{{ project.summary }}</p>
    </div>
    <p class="project-list-meta">
      {{ project.years }}
      {% if project.sponsor %}<span>Funded by {{ project.sponsor }}</span>{% endif %}
    </p>
  </article>
  {% endfor %}
</div>
