# Personal Academic Site

This repository contains a Jekyll-based GitHub Pages site for Abderrahman Ait-Ali.

## Structure

- `_config.yml`: site configuration and navigation.
- `index.md`: homepage content rendered from data files and publication metadata.
- `about.md`, `publications.md`, `projects.md`, `teaching.md`, `contact.md`: top-level site pages.
- `_data/pubs.yml`: structured publication metadata used by the publications page and homepage featured publications.
- `_data/projects.yml`: structured project metadata used by the projects page and homepage featured projects.
- `_data/home.yml`: homepage research interests and featured selections.
- `assets/css/style.scss`: shared site styling overrides on top of the Minima theme.
- `_includes/footer.html`: minimal footer override.
- `files/`: local PDFs and slide decks served by the site.

## Local Development

Install dependencies:

```bash
bundle install
```

Build the site:

```bash
bundle exec jekyll build
```

Preview locally:

```bash
bundle exec jekyll serve
```

The local preview is typically available at `http://127.0.0.1:4000`.

## Content Workflow

- Add or update publications in `_data/pubs.yml`.
- Add or update projects in `_data/projects.yml`.
- Adjust homepage research interests or featured selections in `_data/home.yml`.
- Keep local downloadable assets in `files/` and link to them with `/files/...` paths.
