# Source: Australia Consumer Data Right (Consumer Data Standards)

- **Upstream:** https://github.com/ConsumerDataStandardsAustralia/standards, files `docs/includes/swagger/cds_{banking,energy,telco}.json`
- **Fetched:** 2026-10-26, commit `45f31a807cf6770456eb26aa2c68003d634ea53c` (standards version 1.36.0)
- **Licence:** MIT. The repository's `LICENCE.md` says all specifications are under the MIT licence, "Copyright 2018 Data61"; each description's `info.license` also says MIT.
- **Changes:** none. Each file under `apis/` is the upstream file byte for byte, renamed.

Australia's government data-sharing standard, OpenAPI 3.0.3: the banking, energy and telco sector APIs. They are read-only by design, but some reads are POSTs (for example `POST /banking/accounts/balances` lists balances for named accounts), so the HTTP method alone does not tell the tier. The admin, register, common, DCR and non-bank-lending descriptions in the same folder are not included.
