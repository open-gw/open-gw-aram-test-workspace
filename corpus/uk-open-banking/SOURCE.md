# Source: UK Open Banking Read/Write API

- **Upstream:** https://github.com/OpenBankingUK/read-write-api-specs, files `dist/openapi/{account-info,confirmation-funds,payment-initiation,vrp}-openapi.json`
- **Fetched:** 2026-10-26, commit `484a1795680d9852600247878b9fd2bfe584c0aa` (standard version 4.0.1)
- **Licence:** MIT. The README points to Open Banking Limited's Open Licence (https://www.openbanking.org.uk/open-licence/), which says all specifications are under the MIT licence, "Copyright 2023 Open Banking Limited". Each description's `info.license` names that page.
- **Changes:** none. Each file under `apis/` is the upstream file byte for byte, renamed.

The regulated UK open-banking standard, OpenAPI 3.0.0. Four of its APIs: account information (reads), confirmation of funds, payment initiation and variable recurring payments (VRP), the last two of which move money. The events and event-notification APIs in the same folder are not included.
