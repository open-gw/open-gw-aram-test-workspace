# Corpus: real public API descriptions

Nine sets of real, openly licensed OpenAPI descriptions, each set up as its own Aram
workspace: a `.aram/workspace.yaml`, the descriptions under `apis/`, and a `SOURCE.md` naming
where they came from, when, and under what licence. They are demo material and realistic test
input. No API has overlays or tiers yet: every operation starts unclassified.

## General

| Workspace | API | OpenAPI | Size | Operations | Reads / writes | Licence | Why it is here |
| --- | --- | --- | --- | ---: | --- | --- | --- |
| [`petstore/`](petstore/) | Swagger Petstore | 3.0.4, YAML | 23 KB | 19 | 8 GET / 11 other | Apache-2.0 | Small and familiar: a quick demo, and a first test that a workspace opens |
| [`weather-gov/`](weather-gov/) | US National Weather Service | 3.1.2, JSON | 123 KB | 69 | 69 GET / 0 other | Public domain (US government) | The read-only extreme: every operation is a GET, so tiering should be uniformly low; also the one 3.1 description |
| [`spotify/`](spotify/) | Spotify Web API (community) | 3.0.3, YAML | 286 KB | 97 | 61 GET / 36 other | MIT, derived from Spotify's docs (see its `SOURCE.md`) | Realistic tiering of a consumer API: reads, library and playlist edits, playback control |
| [`stripe/`](stripe/) | Stripe | 3.0.0, YAML | 6.6 MB | 612 | 273 GET / 339 other | MIT | The payments example: charges, refunds, payouts and transfers move money, the highest tiers |
| [`github/`](github/) | GitHub REST | 3.0.3, YAML | 10.3 MB | 1,242 | 651 GET / 591 other | MIT | The size stress case, and realistic tiering at scale: from `GET /zen` to deleting a repository |

## Open banking and open telco

| Workspace | APIs | OpenAPI | Size | Operations | Reads / writes | Licence | Why it is here |
| --- | --- | --- | --- | ---: | --- | --- | --- |
| [`uk-open-banking/`](uk-open-banking/) | UK Open Banking 4.0.1: account information, confirmation of funds, payment initiation, VRP (4 descriptions) | 3.0.0, JSON | 1.4 MB | 83 | 57 GET / 26 other | MIT (Open Banking Limited's Open Licence) | A regulated standard where reads sit beside payment initiation and variable recurring payments, which move money |
| [`au-cdr/`](au-cdr/) | Australia Consumer Data Right 1.36.0: banking, energy, telco (3) | 3.0.3, JSON | 1.0 MB | 60 | 48 GET / 12 other | MIT | Government data sharing, read-only by design, yet some reads are POSTs: the method alone does not tell the tier |
| [`camara/`](camara/) | CAMARA: SIM Swap, Number Verification, Quality on Demand, Device Location (9, from release tags) | 3.0.3, YAML | 407 KB | 25 | 8 GET / 17 other | Apache-2.0 | Telco network APIs (GSMA Open Gateway). SIM Swap and Number Verification are the fraud checks a bank makes before a payment; location is personal data |
| [`tmf622/`](tmf622/) | TM Forum TMF622 Product Ordering 5.0.0 (1) | 3.0.1, YAML | 506 KB | 21 | 4 GET / 17 other | Apache-2.0 | A telco operations API: create, change and cancel orders, plus event-listener callbacks |

For the demo, `uk-open-banking` beside `camara` tells one story: before releasing a payment,
the bank asks the network whether the SIM was just swapped.

Operation counts are what `aram validate` reports; the read/write split is from `aram lint`.

## Verified

On 2026-10-26, each workspace was opened with the Aram CLI built from `open-gw/aram` at
`ab3cbc2`, plus uncommitted work then in progress there (Node 24.21.0):

```sh
aram validate --workspace corpus/<name>
aram lint --fail-on none --workspace corpus/<name>
```

All nine passed `validate` with no parse or reference errors, and `lint` listed every
operation as unclassified, as expected. Time and peak memory for `validate`:

| Workspace | Time | Peak memory |
| --- | ---: | ---: |
| petstore | ~1 s | 124 MB |
| weather-gov | ~1 s | 155 MB |
| spotify | ~2 s | 165 MB |
| stripe | ~5 s | 656 MB |
| github | ~7 s | 1,016 MB |
| uk-open-banking | ~2 s | 273 MB |
| au-cdr | ~1 s | 282 MB |
| camara | ~1 s | 148 MB |
| tmf622 | ~1 s | 252 MB |

CAMARA's descriptions on each repository's `main` branch refer to shared files
(`../common/CAMARA_common.yaml`) and fail `validate` on their own with ARAM-OAS-003, so the
released versions are used. Opening the workspaces in the browser app, from GitHub, was not
tried.

## Left out

- X (Twitter): served under X's developer terms, not an open licence.
- Open Finance Brasil (`OpenBanking-Brasil/openapi`): the repository states no licence.
- Berlin Group NextGenPSD2: its licence could not be confirmed (its download page did not
  load on 2026-10-26).
- FDX: available to members only.

## Licences

Each file under `*/apis/` is the upstream file, unchanged, and keeps its own licence; see the
`SOURCE.md` beside it. The workspace files and these notes are new.
