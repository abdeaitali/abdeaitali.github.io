---
layout: page
title: Projects
permalink: /projects/
---

<div class="page-intro">
  <p>Below is an overview of current and completed projects. Links are provided where a public project page or repository is available.</p>
</div>

## Current Projects

<div class="project-grid">
  {% for project in site.data.projects.current %}
  <article class="project-card" id="{{ project.id }}">
    <p class="project-card-meta">{{ project.years }}</p>
    <h3>{{ project.title }}</h3>
    <p>{{ project.summary }}</p>
    {% if project.sponsor %}
    <p class="project-card-note">Funding: {{ project.sponsor }}</p>
    {% endif %}
    {% if project.url %}
    <p class="project-links"><a href="{{ project.url }}">Project link</a></p>
    {% endif %}
  </article>
  {% endfor %}
</div>

## Completed Projects

<div class="project-grid">
  {% for project in site.data.projects.completed %}
  <article class="project-card" id="{{ project.id }}">
    <p class="project-card-meta">{{ project.years }}</p>
    <h3>{{ project.title }}</h3>
    <p>{{ project.summary }}</p>
    {% if project.url %}
    <p class="project-links"><a href="{{ project.url }}">Project link</a></p>
    {% endif %}
  </article>
  {% endfor %}
</div>
