# CRoB @ ICRA 2027

Website for the ICRA 2027 workshop *Choosing Robot Bodies (CRoB): Specialists and Generalists in Robot Co-Design*.
Served by GitHub Pages at https://crob-icra-2027-workshop.github.io/.

## Editing content

Most edits happen in YAML; no HTML needed.

| What | File |
| --- | --- |
| Date, room, contact email, submission link | `_config.yml` |
| Program | `_data/schedule.yml` |
| Invited speakers | `_data/speakers.yml` |
| Organizers | `_data/organizers.yml` |
| Important dates | `_data/dates.yml` |
| Section text | `_includes/*.html` |
| Styling | `assets/css/style.css` |

Photos go in `assets/img/people/` (square, about 400 px) and are referenced by filename in the `photo` field.
Leave `photo` empty to show the placeholder avatar, and set a speaker `name` to `TBA` for an open slot.

## Running locally

With Docker:

```bash
docker run --rm -it -v "$PWD":/srv/jekyll -p 4000:4000 jekyll/jekyll:pages jekyll serve --host 0.0.0.0
```

With Ruby installed:

```bash
bundle install
bundle exec jekyll serve
```

Then open http://localhost:4000.

## Deploying

GitHub Pages builds the site from the root of `main` on every push
(Settings → Pages → Deploy from a branch → `main` / `/ (root)`).
