# Equation Lab

Live demo: https://itsadityakr.github.io/equation-lab/

This repository holds the generated production build of Equation Lab and nothing
else. Every file here is compiled output: a static `index.html` and a folder of
hashed, minified JavaScript, CSS, and image assets. The entire contents are
regenerated and overwritten whenever a new build is deployed, so any change made
directly in this repository is temporary and will disappear on the next deploy.
The application source is maintained separately at
[itsadityakr/equation-lab-code](https://github.com/itsadityakr/equation-lab-code).

## What this repository is

- The deploy target for GitHub Pages. The contents of this repository are what a
  visitor to the live demo actually downloads and runs.
- A snapshot of one specific build. The hashed filenames under `assets/` change
  from build to build, which is what allows the site to be cached aggressively
  and still update reliably.
- An archive of what was shipped. The commit history is a record of past
  deployments rather than a record of development work.

## What this repository is not

- **Not the source code.** There is no application source, no configuration, and
  no dependency manifest here. The files under `assets/` are minified build
  artifacts and are not intended to be read or edited by hand.
- **Not the issue tracker for the application.** Bugs in the tool itself, feature
  requests, and questions about behaviour belong in the source repository, where
  they can actually be fixed.
- **Not a place to send pull requests.** A pull request against this repository
  would modify build output, and that output is replaced wholesale on the next
  deploy. Changes must be made in the source and then rebuilt.

Contributors should work in
[itsadityakr/equation-lab-code](https://github.com/itsadityakr/equation-lab-code).

## About the app

Equation Lab is a LaTeX formula builder that renders what you write as you write
it. You compose a formula and see the typeset result immediately, without a
compile step or a round trip to a server, which makes it useful for drafting
expressions, checking syntax, and confirming that a formula reads the way you
intended before pasting it into a document.

Rendering is handled by MathJax 3, which the page loads at runtime from a public
CDN (`cdn.jsdelivr.net/npm/mathjax@3`) rather than bundling it into the local
assets. MathJax is configured in `index.html` for inline math delimited by `\(`
and `\)`, with typesetting run at startup. Because of this CDN dependency, the
live page requires network access to that host in order to typeset formulas; the
rest of the application is served entirely from the files in this repository.

The application itself is a single-page build that mounts into a `<div id="root">`
element in `index.html`.

## Contents

```
.
├── index.html                     Build entry point (page title: "Equation Lab")
├── assets/
│   ├── index-CkzgnF-S.js          Minified application bundle (hashed filename)
│   ├── index-CoTE0eoZ.css         Minified stylesheet (hashed filename)
│   └── react-DQICuG8q.png         Favicon referenced by index.html
├── LICENSE
└── README.md
```

The hashed portion of each filename under `assets/` is generated at build time
and will differ in future deploys. Treat the names above as accurate for the
current build only; `index.html` is always the authoritative reference for which
asset files are in use.

Note: `index.html` declares the favicon with `type="image/svg+xml"` while the
file it points at is a PNG. Browsers generally ignore the declared type and load
the image anyway, but the mismatch is worth correcting in the source.

## Deployment

This repository is published with GitHub Pages, which serves the files at the
repository root exactly as they are, with no server-side processing or build step
of its own.

The workflow is: development happens in the source repository, a production build
is produced there, and the resulting output directory is copied into this
repository and committed. Publishing a new version therefore means replacing the
files here with a fresh build rather than editing them.

No CI configuration or automation workflow is committed in this repository, so
the exact publishing mechanism is defined outside of it. Refer to the source
repository for the build and release process.

## Reporting an issue

Please open issues in the source repository:

https://github.com/itsadityakr/equation-lab-code/issues

Issues opened against this repository cannot be fixed here, since the fix has to
land in the source and be rebuilt. When reporting a problem with the live site,
it helps to include the browser and version, the steps to reproduce, the LaTeX
input involved if the problem is with rendering, and any errors shown in the
browser console.

## License

Released under the MIT License. See [LICENSE](LICENSE).

Copyright (c) 2025 Aditya Kumar.

MathJax is loaded from a third-party CDN at runtime and is distributed under its
own license by its own authors.
