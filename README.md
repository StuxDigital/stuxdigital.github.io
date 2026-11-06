<p align="center">
  <picture><source media="(prefers-color-scheme: dark)" srcset="https://global.media.stux.digital/logo-light.png"><source media="(prefers-color-scheme: light)" srcset="https://global.media.stux.digital/logo-dark.png"><img src="https://global.media.stux.digital/logo-dark.png" height="100" alt="Stux.Digital Logo"></picture>
</p>

# Stux.Digital GitHub Pages Redirect

Stux.Digital's GitHub Pages site. Anyone who visits [stuxdigital.github.io](https://stuxdigital.github.io)
is sent straight on to the organisation's profile, [github.com/StuxDigital](https://github.com/StuxDigital).

- One static `index.html`: a meta refresh (with a matching `canonical` link) to
  `https://github.com/StuxDigital`. Every path lands on the profile; paths aren't carried over
- Deployed to GitHub Pages by `.github/workflows/pages.yml` on every push to `main`
- No build step, no dependencies, no tracking

The Stux.Digital sites themselves live on their own domains: [stux.digital](https://stux.digital),
[clients.stux.digital](https://clients.stux.digital) and [status.stux.digital](https://status.stux.digital).

## Changing the target

Edit both URLs in `index.html`:

```html
<meta http-equiv="refresh" content="0;url=https://github.com/StuxDigital" />
<link rel="canonical" href="https://github.com/StuxDigital" />
```

See [CONTRIBUTING.md](CONTRIBUTING.md) for local setup and the release steps.

## Versioning

This project uses [Date Versioning](https://datevers.ing): each release is numbered by its UTC release date as `YY.MM.DD` (for example `26.10.23`), with `-1`, `-2`… for later releases the same day. See [CHANGELOG.md](CHANGELOG.md) for what changed in each release.

Work happens on `test` (or a branch off it), never on `main`. Changes reach `main` only through a pull request from `test`, which needs CI to pass and is reviewed and merged by Leo; the release commit and tag are made on `test` (`git push origin test --tags`) and go live when the pull request is merged.

## License

&copy; 2026 Stux.Group. All rights reserved. This repository is not licensed for reuse or
redistribution.

---

Made by [Stux.Digital](https://github.com/StuxDigital)

*Stux.Digital is part of the [Stux.Group](https://github.com/StuxGroup) Brand of Companies.*

Stux.Digital is operated by Stux Group Ltd, a company registered in England and Wales (company no. 13160574), registered office 82a James Carter Road, Mildenhall, England, IP28 7DE.
