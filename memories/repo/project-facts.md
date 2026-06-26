# Project Facts

This repository is a Jekyll-based GitHub Pages site for Abderrahman Ait-Ali's academic homepage. The site source lives at the repository root. Generated output in `_site/` must not be edited directly.

## Site Structure

- `_config.yml`: Jekyll/minima configuration, site metadata, social handles, and `header_pages` navigation order.
- `index.md`: Home page shell. Uses `layout: default` and includes `_includes/home/hero.html`.
- `research.md`: Research page. Mixes static Markdown/HTML with `site.data.home.research_interests`.
- `publications.md`: Publications page. Renders grouped publication data from `_data/pubs.yml`.
- `projects.md`: Projects page. Renders current and completed projects from `_data/projects.yml`.
- `teaching.md`: Teaching page. Static Markdown page.
- `contact.md`: Contact page. Uses contact data from `_data/home.yml` and links to `/files/cv.pdf`.
- `about.md`: Root Markdown page for biographical/about content if used.
- `_includes/home/*.html`: Homepage sections and reusable Liquid snippets.
- `_includes/footer.html`: Custom footer include.
- `_data/pubs.yml`: Canonical publication data.
- `_data/projects.yml`: Canonical project data.
- `_data/home.yml`: Homepage, research-interest, teaching snapshot, and contact data.
- `assets/css/style.scss`: Main CSS customization layered on top of the `minima` theme.
- `files/`: Static downloads such as PDFs. Link with `/files/...`.
- `images/`: Static images such as `/images/profile.jpeg`.

## Data Schemas

### `_data/pubs.yml`

Top-level publication groups currently used by `publications.md`:

- `preprints`
- `journal_papers`
- `conference_papers`
- `working_papers`
- `other_publications`

Each populated category is a list of year groups:

```yaml
journal_papers:
  - year: 2025
    papers:
      - title: "Publication title"
        authors: ["Ait-Ali, A.", "Coauthor, C."]
        journal: "Journal name"
        volume: "239"
        issue: "9"
        pages: "804-816"
        doi: "10...."
        preprint: "/files/example.pdf"
        pdf: "/files/example.pdf"
        url: "https://..."
        slides: "/files/slides.pdf"
        video: "https://..."
        bibtex_key: "unique-anchor"
        featured: true
        home_summary: "Short homepage summary."
        schema_ld:
          datePublished: "2025-01-01"
          author:
            - name: "Abderrahman Ait-Ali"
```

Fields observed/handled:

- Common: `title`, `authors`, `pages`, `doi`, `url`, `bibtex_key`, `featured`, `home_summary`, `schema_ld`.
- Journal papers: `journal`, `volume`, `issue`, `preprint`, `pdf`, `slides`, `video`.
- Conference papers: `conference`, `journal` fallback, `volume`, `location`, `pages`.
- Preprints/working/other publications: `series`, `number`.

Rendering behavior:

- `publications.md` sorts each category by `year` descending.
- Each paper creates an anchor from `bibtex_key`: `/publications/#bibtex_key`.
- DOI links are generated as `https://doi.org/{{ paper.doi }}`.
- Homepage selected publications currently read only from `site.data.pubs.journal_papers` and display papers where `featured: true`.

### `_data/projects.yml`

Top-level groups:

- `current`
- `completed`

Each project item:

```yaml
- id: "project-anchor"
  title: "Project title"
  years: "2024-2026"
  summary: "Short project summary."
  sponsor: "Funding body"
  url: "https://..."
  featured: true
```

Fields observed/handled:

- Required for stable rendering: `id`, `title`, `years`, `summary`.
- Optional: `sponsor`, `url`, `featured`.

Rendering behavior:

- `projects.md` renders all current and completed projects.
- Project anchors use `id`: `/projects/#project-anchor`.
- Homepage project cards use current projects with `featured: true`.

### `_data/home.yml`

Top-level sections:

- `hero`
- `profile`
- `research_interests`
- `teaching_snapshot`
- `contact`

Schema:

```yaml
hero:
  bio:
    - "Paragraph, HTML allowed."
  affiliations:
    - label: "Institution"
      url: "https://..."
      note: "Role or note"

profile:
  heading: "Short heading"
  paragraphs:
    - "Profile paragraph."

research_interests:
  intro: "Intro text."
  items:
    - title: "Interest"
      summary: "Short description."

teaching_snapshot:
  - title: "Course or supervision area"
    summary: "Short description."
    url: "https://..."

contact:
  email_note: "Intro note."
  emails:
    - label: "VTI"
      address: "name@example.org"
  profiles:
    - label: "Google Scholar"
      url: "https://..."
```

## Common Editing Patterns

- Add or update a publication: edit `_data/pubs.yml`, place downloads in `files/` if needed, use `/files/...` links, then run `bundle exec jekyll build`.
- Feature a publication on the homepage: add `featured: true` and `home_summary` to a journal paper in `_data/pubs.yml`. Note that the current homepage include only checks `journal_papers`.
- Add or update a project: edit `_data/projects.yml`. Use a stable lowercase `id` for anchors. Add `featured: true` only for current projects that should appear on the homepage.
- Update homepage biography, interests, teaching snapshot, or contact blocks: edit `_data/home.yml`.
- Update page prose: edit the matching root Markdown page, preserving existing YAML front matter.
- Update site navigation: edit `header_pages` in `_config.yml`.
- Update visual styling: edit `assets/css/style.scss`; avoid touching generated CSS in `_site/`.
- Add static downloads: place files under `files/` and link with root-relative `/files/...` paths.

## Build Commands

- Install dependencies: `bundle install`
- Build site: `bundle exec jekyll build`
- Preview locally: `bundle exec jekyll serve`

## Do Not Edit

- `_site/`: generated output.
- Dependency/vendor artifacts unless explicitly requested.
