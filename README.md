<h1 align="center">naklios-tex</h1>

<p align="center"><strong>The TeX engine files behind <code>naklios.tex</code>, the shared LaTeX service in NakliOS.</strong></p>
<p align="center">No server-side compile. No account. The PDF is built in your browser.</p>

## Install

Nothing to install. NakliOS downloads these files the first time an app compiles, about 630 MB once per browser.

| Use | Where |
|---|---|
| In NakliOS | Call `naklios.tex.compile()` from an app; see the [app contract](https://github.com/NakliTechie/nakliOS/blob/main/docs/app-contract.md) |
| The files | The [`engine-1.4.1` release](https://github.com/NakliTechie/naklios-tex/releases/tag/engine-1.4.1) |

## Why

You need LaTeX in the browser without sending your paper to a server. These files are `texlyre-busytex`, which is TeX Live 2026 compiled to WebAssembly, copied here without changes so that NakliOS can stream them from one fixed place.

## How it works

`.github/workflows/mirror-assets.yml` copies an upstream release into a release here, one file per asset, and writes `manifest.tsv` with each file's size and SHA-256. A Cloudflare Worker on `naklios.dev` streams those files from this release, because GitHub release files carry no CORS header and two of them exceed GitHub's 100 MB limit for repo files.

Limits: `algorithm2e` and other packages outside the three packs are absent. Add such a file to your project folder.

## License

AGPL-3.0-or-later, the upstream licence. See `LICENSE` and `NOTICE.md`. The source is in each release.
