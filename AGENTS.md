# AGENTS

## Homepage Source

- The homepage source lives in `index.md`.
- Homepage research interests are stored in `_data/home.yml`.
- Featured homepage projects are rendered from `_data/projects.yml`.
- Featured homepage publications are rendered from `_data/pubs.yml`.

## Preferred Tone

- Keep the tone academic, factual, and concise.
- Prefer clear research-oriented language over promotional or marketing-style phrasing.
- Preserve a professional personal-site voice rather than a corporate voice.

## What Not To Change

- Do not migrate the site away from Jekyll/Markdown/Liquid unless explicitly requested.
- Do not introduce a major visual redesign without explicit approval.
- Do not remove the academic framing of the homepage, publications, projects, teaching, or contact pages.
- Do not add decorative UI patterns that make the site feel less formal.
- Do not overwrite unrelated user edits in the worktree.

## Preview And Build

- Install dependencies with `bundle install`.
- Build the site with `bundle exec jekyll build`.
- Preview locally with `bundle exec jekyll serve`.
- The local preview is typically available at `http://127.0.0.1:4000`.

## Publication Formatting Rules

- Publication data lives in `_data/pubs.yml`.
- Keep entries structured in the existing year-group format.
- Use sentence-style titles and preserve accurate author order.
- Avoid broken action links; only include DOI, PDF, slides, video, or preprint links that actually exist.
- Keep homepage-featured publications marked with `featured: true`.
- Use `home_summary` only for concise homepage summaries, not full abstracts.
- Preserve publication anchors via `bibtex_key` so homepage links remain stable.
