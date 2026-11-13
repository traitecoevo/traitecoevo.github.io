# traitecoevo.github.io

Source for <https://traitecoevo.github.io>, the front page for the tools, data and code of the Cornsters: the joint labs of Daniel Falster and Will Cornwell at UNSW Sydney.

The site is built with [Quarto](https://quarto.org) and deployed to GitHub Pages by a GitHub Action on every push to `main`. Pull requests are rendered but not deployed.

## Adding or editing a tool

Tools are listed in YAML files under `data/`, one file per section:

| File | Section |
|---|---|
| `data/austraits.yml` | AusTraits family |
| `data/plant.yml` | plant family |
| `data/havplot.yml` | HAVPlot family |
| `data/ecoacoustics.yml` | ecoacoustics family |
| `data/specieslists.yml` | Species lists & change detection family |
| `data/packages.yml` | Apps & packages (current) |
| `data/retired.yml` | Apps & packages, retired list |
| `data/papers.yml` | Papers & code |

Add an entry to the right file, in the position you want it shown. The fields are documented at the top of `data/austraits.yml` (cards) and `data/retired.yml` (list rows). For example:

```yaml
- name: mypackage
  kind: R package
  status: developing          # stable | developing | experimental
  description: One or two plain-text sentences on what it does.
  repo: mypackage             # under github.com/traitecoevo
  home: https://traitecoevo.github.io/mypackage/
  universe: true              # on traitecoevo.r-universe.dev
```

To show a hex logo, add a PNG of at most 240 px to `assets/logos/` and set `logo: mypackage.png`. Without one, the card shows a two-letter tile.

Section headings, blurbs and the mission statement are in `index.qmd`. The look is all in `assets/style.css`.

## Previewing locally

```sh
quarto preview
```

## How it fits together

- `_quarto.yml` sets `minimal: true`, so Quarto adds no Bootstrap theme; the page uses only `assets/style.css`.
- Each card grid or list in `index.qmd` is a Quarto listing that reads one `data/*.yml` file through a template in `_templates/`.
- `_partials/` holds the header, footer and extra `<head>` tags.

See `PLAN.md` for design decisions and open items.
