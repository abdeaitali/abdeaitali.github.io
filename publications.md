---
layout: page
title: Publications
permalink: /publications/
---

<div class="page-intro">
  <p>This page lists my publications. For the full list, see my <a href="https://scholar.google.com/citations?user=3t1aBqYAAAAJ">Google Scholar profile</a>.</p>
</div>

{% assign categories = "journal_papers,conference_papers,working_papers,other_publications" | split: "," %}
{% assign type_labels = "Peer-reviewed journal articles,Papers in conference proceedings,Working papers,Other publications" | split: "," %}

{% for category in categories %}
  {% assign groups = site.data.pubs[category] | sort: "year" | reverse %}
  {% if groups and groups.size > 0 %}
## {{ type_labels[forloop.index0] }}

    {% for year_group in groups %}
      {% for paper in year_group.papers %}
        {% capture authors_text %}{{ paper.authors | join: ", " }}{% endcapture %}
        {% assign authors_text = authors_text | replace: "Ait‑Ali, A.", "<strong>Ait‑Ali, A.</strong>" %}
        {% assign authors_text = authors_text | replace: "Ait-Ali, A.", "<strong>Ait-Ali, A.</strong>" %}
        {% capture citation %}
          {% if category == "journal_papers" %}
            {{ authors_text }} ({{ year_group.year }}). {{ paper.title }}. *{{ paper.journal }}*{% if paper.volume %}, vol. {{ paper.volume }}{% endif %}{% if paper.issue %}, no. {{ paper.issue }}{% endif %}{% if paper.pages %}, pp. {{ paper.pages }}{% endif %}, {{ year_group.year }}.{% if paper.doi %} DOI: [{{ paper.doi }}](https://doi.org/{{ paper.doi }}){% endif %}{% if paper.preprint %} [Preprint]({{ paper.preprint }}){% endif %}
          {% elsif category == "conference_papers" %}
            {{ authors_text }} ({{ year_group.year }}). {{ paper.title }}. In *{{ paper.conference | default: paper.journal }}*{% if paper.location %}, {{ paper.location }}{% endif %}{% if paper.pages %}, pp. {{ paper.pages }}{% endif %}.{% if paper.pdf %} [PDF]({{ paper.pdf }}){% endif %}{% if paper.slides %} [Slides]({{ paper.slides }}){% endif %}{% if paper.video %} [Video]({{ paper.video }}){% endif %}
          {% elsif category == "working_papers" %}
            {{ authors_text }} ({{ year_group.year }}). {{ paper.title }}. {{ paper.series }}{% if paper.number %}, {{ paper.number }}{% endif %}.{% if paper.pdf %} [PDF]({{ paper.pdf }}){% endif %}{% if paper.slides %} [Slides]({{ paper.slides }}){% endif %}
          {% else %}
            {{ authors_text }} ({{ year_group.year }}). {{ paper.title }}. {{ paper.series }}{% if paper.number %}, {{ paper.number }}{% endif %}.{% if paper.pdf %} [PDF]({{ paper.pdf }}){% endif %}{% if paper.slides %} [Slides]({{ paper.slides }}){% endif %}{% if paper.video %} [Video]({{ paper.video }}){% endif %}
          {% endif %}
        {% endcapture %}
        {% if citation != "" %}
- {{ citation | strip }}
        {% endif %}
      {% endfor %}
    {% endfor %}
  {% endif %}
{% endfor %}
