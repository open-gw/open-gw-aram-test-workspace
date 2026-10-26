# Corpus: real public API descriptions

Five real, openly licensed OpenAPI descriptions, each set up as its own Aram workspace: a
`.aram/workspace.yaml`, the description under `apis/`, and a `SOURCE.md` naming where it came
from, when, and under what licence. They are demo material and realistic test input. No API
has overlays or tiers yet: every operation starts unclassified.

| Workspace | API | OpenAPI | Size | Operations | Reads / writes | Licence | Why it is here |
| --- | --- | --- | --- | ---: | --- | --- | --- |
| [`petstore/`](petstore/) | Swagger Petstore | 3.0.4, YAML | 23 KB | 19 | 8 GET / 11 other | Apache-2.0 | Small and familiar: a quick demo, and a first test that a workspace opens |
| [`weather-gov/`](weather-gov/) | US National Weather Service | 3.1.2, JSON | 123 KB | 69 | 69 GET / 0 other | Public domain (US government) | The read-only extreme: every operation is a GET, so tiering should be uniformly low; also the one 3.1 and the one JSON description |
| [`spotify/`](spotify/) | Spotify Web API (community) | 3.0.3, YAML | 286 KB | 97 | 61 GET / 36 other | MIT, derived from Spotify's docs (see its `SOURCE.md`) | Realistic tiering of a consumer API: reads, library and playlist edits, playback control |
| [`stripe/`](stripe/) | Stripe | 3.0.0, YAML | 6.6 MB | 612 | 273 GET / 339 other | MIT | The payments example: charges, refunds, payouts and transfers move money, the highest tiers |
| [`github/`](github/) | GitHub REST | 3.0.3, YAML | 10.3 MB | 1,242 | 651 GET / 591 other | MIT | The size stress case, and realistic tiering at scale: from `GET /zen` to deleting a repository |

Operation counts are what `aram validate` reports; the read/write split is from `aram lint`.

## Verified

On 2026-10-26, each workspace was opened with the Aram CLI built from `open-gw/aram` at
`ab3cbc2`, plus uncommitted work then in progress there (Node 24.21.0):

```sh
aram validate --workspace corpus/<name>
aram lint --fail-on none --workspace corpus/<name>
```

All five passed `validate` with no parse or reference errors, and `lint` listed every
operation as unclassified, as expected. Time and peak memory for `validate`:

| Workspace | Time | Peak memory |
| --- | ---: | ---: |
| petstore | ~1 s | 124 MB |
| weather-gov | ~1 s | 155 MB |
| spotify | ~2 s | 165 MB |
| stripe | ~5 s | 656 MB |
| github | ~7 s | 1,016 MB |

Opening them in the browser app, from GitHub, was not tried.

## Left out

X (Twitter)'s description is served under X's developer terms, not an open licence, so it is
not here.

## Licences

Each file under `*/apis/` is the upstream file, unchanged, and keeps its own licence; see the
`SOURCE.md` beside it. The workspace files and these notes are new.
