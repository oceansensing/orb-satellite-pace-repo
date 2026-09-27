# orb-satellite-pace-repo

The University of Delaware ORB lab's **PACE** products: a data repository of the oceansensing ocean map system, with its own
Pages site, its own schedule and its own gigabyte, and no code of its own.

**Nothing to publish yet**: its upstream is not live (see PLAN). `PLAN.md` is the founding plan; `CLAUDE.md` carries what must not be
got wrong and the shared doc doctrine.

## What it publishes

ORB's PACE ocean-color products, beginning with `pace_abs` (total absorption, backscattering and phytoplankton absorption at 19 wavelengths, 351-711 nm, global at 1/24 degree), **once the server carries them live**.

These products are published **operationally but not drawn on the website's map**; the map's status
line still reports them when they fall behind, which is how their health stays visible.

## Where the data comes from

The University of Delaware's Ocean Remote sensing laboratory (ORB) serves its processed products openly from its own ERDDAP, `https://basin.ceoe.udel.edu/erddap`, with no login. Every dataset there carries the same license text: the data *"may be used and redistributed for free but is not intended for legal use, since it may contain inaccuracies"*. More of that server's products are expected to join (the owner, 2026-09-27), which is why the site's fetcher, `scripts/fetch-erddap.py`, is written for the server and takes a product as a row. **Read 2026-09-27**: all three PACE datasets there (`pace_abs`, `pace_kd`, `pace_misc`, "PACE provisional data downloaded from OCBG, processed by UD ORB") hold one month, 2024-09-01 to 2024-09-30, and nothing since. There is nothing to fetch on a schedule, so the owner's call was to set this repository up (documents, workflow, secrets) and publish nothing until the data is live.

## How it runs

The orchestrator (the site's private `pipeline/`), the fetchers and the
published-file contract all come from `oceansensing.github.io`, checked out at
run time. This repository carries `pipeline/products.toml` and its publish
workflow, and nothing else executable. Each run publishes to GitHub Pages and
to Cloudflare R2 from one build. Related repositories: the other University of Delaware ORB repositories, `orb-satellite-viirs-repo`, `orb-satellite-goes-repo` and `orb-satellite-pace-repo`.

**Which document gets what, and what "update docs" means across all
twenty repositories, is the doctrine block at the top of `CLAUDE.md`**: the
same text in all twenty, held equal by the site's `check:docs`.

## Structure

```
README.md       what this is
CLAUDE.md       what must not be got wrong, and the shared doc doctrine
PLAN.md         the founding plan and running record
DECISIONS.md    dated one-way decisions, D1 onward
pipeline/       products.toml, the declaration the orchestrator reads
.github/        the publish workflow
```
