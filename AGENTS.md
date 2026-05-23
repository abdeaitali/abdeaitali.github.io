# AI Agent Instructions

This repository is a Jekyll-based GitHub Pages site for a personal academic homepage.

## Key facts

- Site source is the repository root and `_includes`, `_data`, `assets`, `files`, and Markdown pages such as `index.md`, `about.md`, `publications.md`, `projects.md`, `teaching.md`, and `contact.md`.
- The `_site/` directory is generated output. Do not edit files inside `_site/` directly.
- Data-driven content is stored in `_data/pubs.yml`, `_data/projects.yml`, and `_data/home.yml`.
- Styling is customized in `assets/css/style.scss` on top of the `minima` theme from `_config.yml`.

## Workflow

- Use `bundle install` to install dependencies.
- Use `bundle exec jekyll build` to build the site.
- Use `bundle exec jekyll serve` to preview locally.
- Changes belong in source files and data files, not in `_site/`.

## What to edit

- Update publications via `_data/pubs.yml`.
- Update projects via `_data/projects.yml`.
- Update homepage selections via `_data/home.yml`.
- Update page content via the corresponding `.md` file in the repository root.
- Keep downloads in `files/` and link to them using `/files/...` paths.

## Notes for agents

- Preserve existing Jekyll front matter and markdown structure.
- Prefer adding or updating source markdown/data files over touching generated output.
- If asked about the site structure, refer to `README.md` for higher-level documentation.
