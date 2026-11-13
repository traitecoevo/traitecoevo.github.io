# Plan

Started 2026-11-13. Replaces the 2016 page at this address (whose repository had been deleted; its history is kept in this repo).

## Decisions

- **Sections**, in order: AusTraits family, plant family, HAVPlot family, ecoacoustics family, species lists & change detection family, Apps & packages (current, then retired), Papers & code, About. The families come first because they are the group's main current programmes.
- **Quarto, not Jekyll.** The group already uses Quarto (Overstorey, APD, traits.build book). Jekyll on GitHub Pages is pinned to an old version and needs a Ruby toolchain to preview. Deployment is by GitHub Action (`.github/workflows/publish.yml`) with Pages set to build from Actions, not from a branch.
- **No Bootstrap.** `_quarto.yml` sets `minimal: true`; all styling is in `assets/style.css`. `.d-none` and `.listing-no-matching` are hidden in that stylesheet because Quarto's listing markup expects Bootstrap to hide them.
- **Content lives in data, not markup.** Tools are in `data/*.yml`, one file per section; section text is in `index.qmd`. Cards and rows are rendered by `_templates/cards.ejs` and `_templates/rows.ejs`.
- **Papers & code lists only papers with reproducible code** in a public repository. Full publication lists are left to the Google Scholar profiles linked in that section.
- **Only public repositories get a GitHub link.** HAVPlot's repositories (`havplot.build`, `plots.build`) are private, so their cards set `private: true` and show "Not yet public".
- **Logos are copied into `assets/logos/`**, downscaled to at most 240 px, not hotlinked from package repositories.

## Invariants

- **Do not indent HTML in `_templates/*.ejs`.** Quarto passes template output through Markdown, so a line with four leading spaces becomes a code block. This has already broken the cards once.
- Anchor ids `austraits`, `plant`, `havplot`, `ecoacoustics`, `specieslists`, `packages`, `papers` and `about` are linked from the header, the hero and possibly from elsewhere; keep them stable.
- The repo must not contain a top-level folder named after an existing project site (for example `plant/` or `APCalign/`), because it would shadow `traitecoevo.github.io/<project>/`.

## Open

1. Check every blurb with the tool's maintainer; several were written from READMEs.
2. Will's lab: link a members page if willcornwell.org has one (currently links the home page).
3. When HAVPlot repositories become public, remove `private: true` from `data/havplot.yml`.
4. Logos for tools that have none (plant, APD, odelia, ...).
5. Decide on public repositories left off the page: `floracle` (nascent), `austraits.org`, `austraits-api`, `austraits.portal`, `APCalign-app`, `traits.build-book`, `traits.build-template` (all reachable through other cards), `taxonAlign.dataprep`, `plant-meta`, `austraits-meta`, `logpile`, `kossyphen`, `spatRast`, `sizedist`, `cornsters_australian_annuals`, `aus_trait_gradients`, `australian_plant_endemism`, `aus_gbif_clean`, `fg_spectral_diversity`, `AI-species-catalogue`, `shinystats`, `austraits-python`, `austraits-bigdata-lessons`, `sTEP_overlap`, `richness`, `tree_rings`, `mortality_models`, `experimentr`, `traitecoevo_project_templates`, `remake_baad_example`, `plant_talk`, `data_versioning`, `callr`, `drat` and `threatened_species_traits` (projects, not papers; perhaps a future "Data & projects" list), and the forks.
6. Papers & code: add DOIs for `competition_kernels`, `mortality_bci`, `reproductive_allocation_kuringgai` and `colors_in_citizen_science`, update `growth_trajectories` from the bioRxiv preprint to the published version, and add more recent papers with code (many sit in personal or student accounts, not this org).
7. Keep this page and `traitecoevo.r-universe.dev` (`packages.json` in that repo) in step: a card with `universe: true` must be in the registry. [traitecoevo.r-universe.dev#3](https://github.com/traitecoevo/traitecoevo.r-universe.dev/pull/3) adds saltbush, rabbit, birdnetprocess, EcoacousticUtilities, taxonAlign, odelia, regnans, fieldtrial, phylloptim, framecpp and responses.build. Once it is merged and they build, set `universe: true` on their cards (the ecoacoustic_utilities card in `data/ecoacoustics.yml` already sets `package: EcoacousticUtilities`).
8. Possible later: a scheduled link check, and a list of recent releases pulled from GitHub.
