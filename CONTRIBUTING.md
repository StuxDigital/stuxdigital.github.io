<p align="center">
  <picture><source media="(prefers-color-scheme: dark)" srcset="https://global.media.stux.digital/logo-light.png"><source media="(prefers-color-scheme: light)" srcset="https://global.media.stux.digital/logo-dark.png"><img src="https://global.media.stux.digital/logo-dark.png" height="80" alt="Stux.Digital Logo"></picture>
</p>

# Contributing to Stux.Digital GitHub Pages Redirect

`stuxdigital.github.io` is a minimal GitHub Pages redirect page (`index.html`) that forwards visitors from `stuxdigital.github.io` to [github.com/StuxDigital](https://github.com/StuxDigital). This document is for anyone working on the redirect page itself.

## Local setup

There's no build step or dependencies — just open `index.html` in a browser, or serve the directory with any static file server, e.g.:

```bash
python3 -m http.server 8000
```

## Project conventions

- Single static `index.html` — no framework, no build step, no backend.
- Keep it minimal; this repo exists only to redirect GitHub Pages traffic.

## Branches and going live

- **`main` is what's live.** Nothing is pushed to it directly: it only changes when a pull request from `staging` is merged, and it needs CI to pass.
- **`staging` is the last check before live.** It only changes when a pull request from `test` is merged. It isn't deployed anywhere of its own; deploys stay on `main`.
- **Work happens on `test`**, or on a feature branch off `test` that's merged back into it. Releases are made on `test` too; `commit.sh` / `commit.bat` refuse to run on `staging` or `main`.
- **Going live:** push `test` with its tag (`git push origin test --tags`), open a pull request into staging (`gh pr create --base staging --head test`), check staging once it's merged, then open one from staging into main (`gh pr create --base main --head staging`). Leo reviews and merges both.

## Versioning

This project uses [Date Versioning](https://datevers.ing). To release:

1. Add a `## vYY.MM.DD` entry at the top of `CHANGELOG.md`, with its sections in this order: Added, Changed, Fixed, Removed, Security, Deprecated.
2. Set `VERSION.md` to the same bare version (no `v`): today's **UTC** date as `YY.MM.DD`, or `YY.MM.DD-1`, `-2`… for later releases the same UTC day. Never a future date. Use UTC, not local time: just after midnight in the UK it is still the previous day in UTC.
3. Run `bash tests/version.sh`.
4. Run `./commit.sh` (or `commit.bat` on Windows). It checks the version, commits and tags `vYY.MM.DD`, and never pushes.

## Before committing

- Open `index.html` in a browser and confirm the redirect fires correctly
