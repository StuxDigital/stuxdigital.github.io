# Changelog

All notable changes to stuxdigital.github.io are documented here.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Date Versioning](https://datevers.ing) since v26.10.23 (`YY.MM.DD`, the UTC release date, with `-1`, `-2`… for later releases the same day); earlier releases used [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## v26.11.06-2

### Added

- CI (`.github/workflows/ci.yml`) runs `tests/version.sh` on pushes to `main` and `test` and on pull requests into `main`, so a pull request has checks to pass

### Changed

- `commit.sh` and `commit.bat` end by telling you to push `test` (with the new tag) and open a pull request from `test` into `main`, instead of pushing `main`

## v26.11.06-1

### Changed

- Work happens on a `test` branch: changes reach `main` only through a pull request from `test`, and release commits and tags are made on `test`. `README.md` and `CONTRIBUTING.md` (a new Branches section) say so

## v26.11.06

### Changed

- `README.md` is rewritten to describe this repo, Stux.Digital GitHub Pages Redirect, instead of generic template instructions: it sends stuxdigital.github.io to github.com/StuxDigital (every path lands on the profile; paths aren't carried over), deployed by `.github/workflows/pages.yml`
- The logo in `README.md` and `CONTRIBUTING.md` uses the light/dark `<picture>` style

### Fixed

- `README.md`'s license said "Feel free to use this template"; it now matches the other Stux.Digital repos: © Stux.Group, all rights reserved

## v26.10.23

### Added

- `tests/version.sh`, which checks that `VERSION.md` is a valid Date Version, a real calendar date not in the future, and the same as the newest entry in this changelog

### Changed

- Switched from Semantic Versioning to [Date Versioning](https://datevers.ing): releases are numbered by their UTC release date as `YY.MM.DD`, with `-1`, `-2`… for later releases the same day. This release follows v1.0.0
- `commit.sh` and `commit.bat` refuse a `VERSION.md` that isn't a valid Date Version or is dated in the future (UTC), and warn when it's dated before today
- `README.md` and `CONTRIBUTING.md` describe Date Versioning and the release steps

## v1.0.0

### Added
- Initial GitHub Pages redirect repo for Stux.Digital, redirecting `stuxdigital.github.io` to `github.com/StuxDigital`, deployed through GitHub Actions (`.github/workflows/pages.yml`) — `VERSION.md`/`CHANGELOG.md`/`CONTRIBUTING.md`/`commit.sh`+`commit.bat`/`.gitignore` added, following the standard release-flow convention used across other Stux.Group family repos.
