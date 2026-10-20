# CRoB @ ICRA 2027 website

Single-page Jekyll site for the ICRA 2027 workshop "Choosing Robot Bodies (CRoB)". GitHub Pages builds it natively from `main` root (no Actions, no custom plugins; only `github-pages`-whitelisted features).

## Layout
- Content data: `_data/schedule.yml`, `speakers.yml`, `organizers.yml`, `dates.yml`. Prefer editing YAML over HTML.
- Logistics (date, room, contact email, submission link): `_config.yml`.
- Section markup and prose: `_includes/*.html`, assembled in `index.html`. Shared person card: `_includes/person.html`.
- Styling: `assets/css/style.css` (color tokens for light and dark mode at top). Bootstrap 5.3.3 from jsDelivr.
- Photos: `assets/img/people/<lastname>.jpg`, 400x400 square JPEG, face centered. Empty `photo` field shows `placeholder.svg`. Speaker `name: "TBA"` renders an open slot.

## Content rules
- Source of truth for content: `docs/ICRA_2027_Workshop_proposal.pdf`. `docs/` is gitignored and must stay private; never commit or link it.
- Unconfirmed info shows as "TBA"; speakers stay labelled as invited and pending confirmation until confirmed.
- No individual organizer emails on the site; only the single `contact_email`.
- Load the `przystupa-voice` skill before writing or editing site prose.

## Build and preview (no local Ruby; use Docker)
```bash
# Live preview at http://localhost:4000
docker run --rm --name crob-preview -v "$PWD":/srv/jekyll -p 4000:4000 jekyll/jekyll:pages \
  jekyll serve --host 0.0.0.0 --watch --force_polling --destination /tmp/_site
```
Building into the repo from Docker leaves root-owned `_site/`, `.jekyll-cache/`, and `Gemfile.lock`; build to a container path (as above) to avoid that.
