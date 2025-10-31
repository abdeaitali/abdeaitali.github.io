---
layout: page
title: Publications
permalink: /publications/
---

## Journal papers

A list of peer-reviewed publications (newest first). For a complete list, see my [Google Scholar profile](https://scholar.google.com/citations?user=3t1aBqYAAAAJ).

{% for year_group in site.data.pubs.journal_papers %}
### {{ year_group.year }}
{% for paper in year_group.papers %}
- {{ paper.authors | join: ", " }}. ({{ year_group.year }}). {{ paper.title }}. *{{ paper.journal }}*{% if paper.volume %}, {{ paper.volume }}{% endif %}{% if paper.issue %}({{ paper.issue }}){% endif %}{% if paper.pages %}, {{ paper.pages }}{% endif %}.
  <div class="chips">
    <a href="https://doi.org/{{ paper.doi }}">DOI</a>
    {% if paper.preprint %}<a href="{{ paper.preprint }}">Preprint</a>{% endif %}
    <a href="/files/pubs.bib#{{ paper.bibtex_key }}">BibTeX</a>
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

## Working papers

{% for year_group in site.data.pubs.working_papers %}
{% for paper in year_group.papers %}
- {{ paper.authors | join: ", " }}. ({{ year_group.year }}). {{ paper.title }}. *{{ paper.series }}*, {{ paper.number }}.
  <div class="chips">
    {% if paper.pdf %}<a href="{{ paper.pdf }}">PDF</a>{% endif %}
    <a href="/files/pubs.bib#{{ paper.bibtex_key }}">BibTeX</a>
  </div>
{% endfor %}
{% endfor %}
- Ait‑Ali, A., Lidén, T. (2021). Minimal utilization rates for railway maintenance windows: a cost‑benefit approach. *VTI Working Papers Series*, 2021:8. [[PDF](http://urn.kb.se/resolve?urn=urn:nbn:se:vti:diva-17178)] [[Slides](https://github.com/abdeaitali/abdeaitali.github.io/raw/master/files/slides/scba21.pdf)]

## Other publications

- Ait‑Ali, A., Peterson, A. (2024). *Värdering av trafikinformationsnyttor i tågtrafiken (VTT): slutrapport*. VTI‑rapport. [[PDF](https://urn.kb.se/resolve?urn=urn:nbn:se:vti:diva-20934)]
- Ait‑Ali, A. (2020). Methods for Capacity Allocation in Deregulated Railway Markets. *Linköping Studies in Science and Technology*, Dissertation No. 2101. [[PDF](https://doi.org/10.3384/diss.diva-170193)] [[Thesis](https://github.com/abdeaitali/abdeaitali.github.io/raw/master/files/phdthesis.pdf)] [[Slides](https://github.com/abdeaitali/abdeaitali.github.io/raw/master/files/slides/phd.pdf)] [[Video](https://youtu.be/5EsgU053MHU)]
