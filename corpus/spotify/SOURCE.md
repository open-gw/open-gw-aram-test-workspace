# Source: Spotify Web API (community description)

- **Upstream:** https://github.com/sonallux/spotify-web-api, file `fixed-spotify-open-api.yml`
- **Fetched:** 2026-10-26, commit `f1d6138cd0b2bcc8dbd8567e28af97bf68eb7d7c`
- **Licence:** MIT (repository licence), with a caveat
- **Changes:** none. The file under `apis/` is the upstream file byte for byte, renamed.

**Caveat:** this is not Spotify's own file. sonallux generates it from Spotify's public Web API reference documentation and applies fixes; the repository is MIT, but the operation names, summaries and descriptions are derived from Spotify's documentation, whose own terms (https://developer.spotify.com/terms/) are not an open licence. Treat it as test input; do not present it as Spotify's official description. The "fixed" variant is used rather than `official-spotify-open-api.yml` because it corrects known errors in the generated description.
