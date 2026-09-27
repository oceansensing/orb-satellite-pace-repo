# orb-satellite-pace-repo: the founding plan and running record

The University of Delaware ORB lab's **PACE** products. Created on GitHub by the owner and given its documents by the site's
`pipeline/scaffold/new-origin.py`. **Nothing to publish yet**: its upstream is not live (see PLAN).

## What it is for

ORB's PACE ocean-color products, beginning with `pace_abs` (total absorption, backscattering and phytoplankton absorption at 19 wavelengths, 351-711 nm, global at 1/24 degree), **once the server carries them live**.

## Where the data comes from

The University of Delaware's Ocean Remote sensing laboratory (ORB) serves its processed products openly from its own ERDDAP, `https://basin.ceoe.udel.edu/erddap`, with no login. Every dataset there carries the same license text: the data *"may be used and redistributed for free but is not intended for legal use, since it may contain inaccuracies"*. More of that server's products are expected to join (the owner, 2026-09-27), which is why the site's fetcher, `scripts/fetch-erddap.py`, is written for the server and takes a product as a row. **Read 2026-09-27**: all three PACE datasets there (`pace_abs`, `pace_kd`, `pace_misc`, "PACE provisional data downloaded from OCBG, processed by UD ORB") hold one month, 2024-09-01 to 2024-09-30, and nothing since. There is nothing to fetch on a schedule, so the owner's call was to set this repository up (documents, workflow, secrets) and publish nothing until the data is live.

## Open

1. Watch the server for live PACE data (`allDatasets` lists each dataset's time span).
2. Then: products in the site's contract, `products.toml`, rehearse, dispatch, schedule.

## The workflow's packages come from the site — 2026-09-27

The publish workflow installs `site/scripts/requirements-erddap.txt`, one file
per fetcher family, instead of naming packages in its own `pip install`
line. Dependabot reads requirements files and never a workflow line: an
inline pin elsewhere had carried `requests` 2.32.3, a version with two
advisories, unflagged. The site's `check:docs` now refuses an inline package
here. Not yet run here: this repository publishes nothing until PACE is live on
the server, so no run has been dispatched.
