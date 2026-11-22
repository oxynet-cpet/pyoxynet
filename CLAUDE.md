# pyoxynet: Claude briefing

The open-source package behind the Oxynet papers: two frozen research models, a CNN and an LSTM,
run with LiteRT, so no TensorFlow is needed to use them. Package source is `pyoxynet/pyoxynet/`
(`pyoxynet/pyproject.toml`); the docs are on ReadTheDocs (`docs/`, Furo); tests run on Linux,
Windows and macOS (`.github/workflows/tests.yml`).

## Rules

- **The models are frozen.** They are never retrained or replaced in place: a different model
  is a new file and a new major version (`pyoxynet/pyoxynet/models/README.md` records where
  each file came from and its checksum).
- **The hosted Oxynet API is a separate service.** Nothing from it is ported into this package:
  no production weights, parser or analyses. Statements about it point at it; they never
  describe it as part of pyoxynet.
- **Citations come from Crossref, PubMed or this repository's docs**, never from memory.
- **Words:** no em dashes in anything a user reads; never a confidence percentage; oscillatory
  ventilation, wherever it is mentioned, is beta (one heart-failure cohort, transportability
  untested).

## Releasing

- `master` needs an approving review, so the maintainer merges. Bump `version` in
  `pyoxynet/pyproject.toml`, then a `v*` tag runs `.github/workflows/release.yml`, which builds
  and publishes to PyPI by trusted publishing from the `pypi` environment.
- **Check alignment before tagging, not after** (maintainer, 2026-11-20). Read every statement
  about the hosted API (`README.md`, `pyoxynet/README.md`, which is the PyPI page, and
  `docs/*.rst`) against what the API serves today (`https://app.oxynet.net/llms-full.txt`),
  and check the citations. A page elsewhere that states pyoxynet's version follows only once
  PyPI has the release. Maintainers also follow the cross-repo release checklist of the Oxynet
  workspace.
- **Keep it proportionate:** fix what is false; minor wording drift is noted once and left.
