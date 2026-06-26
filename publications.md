---
layout: page
title: Publications
permalink: /publications/
---

<div class="page-intro">
  <p>This page lists my publications. For the full list, see my <a href="https://scholar.google.com/citations?user=3t1aBqYAAAAJ">Google Scholar profile</a>.</p>
</div>

{% assign journal_groups = site.data.pubs.journal_papers | sort: "year" | reverse %}
{% assign conference_groups = site.data.pubs.conference_papers | sort: "year" | reverse %}
{% assign working_groups = site.data.pubs.working_papers | sort: "year" | reverse %}
{% assign report_groups = site.data.pubs.other_publications | sort: "year" | reverse %}

## Featured publications
---

<div class="publication-list publication-featured-list">
{% for year_group in journal_groups %}
  {% for paper in year_group.papers %}
    {% if paper.featured %}
      {% include publication-item.html paper=paper year=year_group.year category="journal_papers" %}
    {% endif %}
  {% endfor %}
{% endfor %}
</div>

## Journal articles
---

<div class="publication-list">
{% for year_group in journal_groups %}
  {% for paper in year_group.papers %}
    {% include publication-item.html paper=paper year=year_group.year category="journal_papers" %}
  {% endfor %}
{% endfor %}
</div>

<details class="publication-section">
<summary>Conference proceedings</summary>
<div class="publication-list">
{% for year_group in conference_groups %}
  {% for paper in year_group.papers %}
    {% include publication-item.html paper=paper year=year_group.year category="conference_papers" %}
  {% endfor %}
{% endfor %}
</div>
</details>

<details class="publication-section">
<summary>Working papers & reports</summary>
<div class="publication-list">
{% for year_group in working_groups %}
  {% for paper in year_group.papers %}
    {% include publication-item.html paper=paper year=year_group.year category="working_papers" %}
  {% endfor %}
{% endfor %}
{% for year_group in report_groups %}
  {% for paper in year_group.papers %}
    {% include publication-item.html paper=paper year=year_group.year category="other_publications" %}
  {% endfor %}
{% endfor %}
</div>
</details>
