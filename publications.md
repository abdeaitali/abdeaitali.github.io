---
layout: page
title: Publications
permalink: /publications/
---

<div class="page-intro">
  <p>This page collects peer-reviewed journal papers, conference papers, working papers, and other publications. Entries are grouped by publication type and listed in reverse chronological order.</p>
</div>

## Journal papers

A list of peer-reviewed publications (newest first). Action chips are provided where available (DOI, PDF, slides). For a complete list, see my [Google Scholar profile](https://scholar.google.com/citations?user=3t1aBqYAAAAJ).

{% assign sorted_papers = site.data.pubs.journal_papers | sort: "year" | reverse %}

{% for year_group in sorted_papers %}
{% for paper in year_group.papers %}
{% assign title_last = paper.title | slice: -1, 1 %}
- <span id="{{ paper.bibtex_key }}"></span>{{ paper.authors | join: ", " }} ({{ year_group.year }}). {{ paper.title }}{% unless title_last == "." or title_last == "?" or title_last == "!" %}.{% endunless %} *{{ paper.journal }}*{% if paper.volume %}, {{ paper.volume }}{% endif %}{% if paper.issue %}({{ paper.issue }}){% endif %}{% if paper.pages %}, {{ paper.pages }}{% endif %}.
  <div class="chips">
    <a href="https://doi.org/{{ paper.doi }}">DOI</a>
    {% if paper.preprint %}<a href="{{ paper.preprint }}">Preprint</a>{% endif %}
  </div>
  {% if paper.schema_ld %}
  <script type="application/ld+json">
  {
    "@context": "https://schema.org",
    "@type": "ScholarlyArticle",
    "headline": {{ paper.title | jsonify }},
    "author": [
      {% for author in paper.schema_ld.author %}
      {"@type": "Person", "name": {{ author.name | jsonify }}}{% unless forloop.last %},{% endunless %}
      {% endfor %}
    ],
    "datePublished": "{{ paper.schema_ld.datePublished }}",
    "isPartOf": {
      "@type": "Periodical",
      "name": {{ paper.journal | jsonify }}{% if paper.volume %},
      "volumeNumber": {{ paper.volume | jsonify }}{% endif %}
    },
    "sameAs": "https://doi.org/{{ paper.doi }}",
    "url": "https://doi.org/{{ paper.doi }}"
  }
  </script>
  {% endif %}
{% endfor %}
{% endfor %}

## Conference papers

{% assign sorted_conf_papers = site.data.pubs.conference_papers | sort: "year" | reverse %}
{% for year_group in sorted_conf_papers %}
{% for paper in year_group.papers %}
{% assign title_last = paper.title | slice: -1, 1 %}
- <span id="{{ paper.bibtex_key }}"></span>{{ paper.authors | join: ", " }} ({{ year_group.year }}). {{ paper.title }}{% unless title_last == "." or title_last == "?" or title_last == "!" %}.{% endunless %} *{{ paper.conference }}*, {{ paper.location }}.
  {% if paper.pdf or paper.slides or paper.video %}
  <div class="chips">
    {% if paper.pdf %}<a href="{{ paper.pdf }}">PDF</a>{% endif %}
    {% if paper.slides %}<a href="{{ paper.slides }}">Slides</a>{% endif %}
    {% if paper.video %}<a href="{{ paper.video }}">Video</a>{% endif %}
  </div>
  {% endif %}
{% endfor %}
{% endfor %}

## Working papers

{% assign sorted_working_papers = site.data.pubs.working_papers | sort: "year" | reverse %}
{% for year_group in sorted_working_papers %}
{% for paper in year_group.papers %}
{% assign title_last = paper.title | slice: -1, 1 %}
- <span id="{{ paper.bibtex_key }}"></span>{{ paper.authors | join: ", " }} ({{ year_group.year }}). {{ paper.title }}{% unless title_last == "." or title_last == "?" or title_last == "!" %}.{% endunless %} *{{ paper.series }}*, {{ paper.number }}.
  {% if paper.pdf or paper.slides %}
  <div class="chips">
    {% if paper.pdf %}<a href="{{ paper.pdf }}">PDF</a>{% endif %}
    {% if paper.slides %}<a href="{{ paper.slides }}">Slides</a>{% endif %}
  </div>
  {% endif %}
{% endfor %}
{% endfor %}

## Other publications

{% assign sorted_other_pubs = site.data.pubs.other_publications | sort: "year" | reverse %}
{% for year_group in sorted_other_pubs %}
{% for paper in year_group.papers %}
{% assign title_last = paper.title | slice: -1, 1 %}
- <span id="{{ paper.bibtex_key }}"></span>{{ paper.authors | join: ", " }} ({{ year_group.year }}). {{ paper.title }}{% unless title_last == "." or title_last == "?" or title_last == "!" %}.{% endunless %} {% if paper.thesis %}*{{ paper.series }}*, {{ paper.number }}.{% else %}*{{ paper.series }}*.{% endif %}
  {% if paper.pdf or paper.thesis or paper.slides or paper.video %}
  <div class="chips">
    {% if paper.thesis %}<a href="{{ paper.pdf }}">Thesis</a>{% elsif paper.pdf %}<a href="{{ paper.pdf }}">PDF</a>{% endif %}
    {% if paper.slides %}<a href="{{ paper.slides }}">Slides</a>{% endif %}
    {% if paper.video %}<a href="{{ paper.video }}">Video</a>{% endif %}
  </div>
  {% endif %}
{% endfor %}
{% endfor %}
