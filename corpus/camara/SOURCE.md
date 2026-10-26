# Source: CAMARA network APIs

CAMARA is the Linux Foundation project that defines the telco network APIs behind GSMA Open Gateway. Each API lives in its own repository; these are taken from release tags, whose descriptions are self-contained.

| File under `apis/` | Upstream | Release | Commit |
| --- | --- | --- | --- |
| `sim-swap.openapi.yaml`, `sim-swap-subscriptions.openapi.yaml` | https://github.com/camaraproject/SimSwap | `r3.3` | `6008716efcbe055a6ef71ef74df59b2d53e70b30` |
| `number-verification.openapi.yaml` | https://github.com/camaraproject/NumberVerification | `r4.2` | `193c5713f1a1761a7db33743a29ce853e2699ed6` |
| `quality-on-demand.openapi.yaml`, `qos-profiles.openapi.yaml`, `qos-provisioning.openapi.yaml` | https://github.com/camaraproject/QualityOnDemand | `r3.2` | `9cb179fd3b63f43d564c76689295cd681e723548` |
| `location-retrieval.openapi.yaml`, `location-verification.openapi.yaml`, `geofencing-subscriptions.openapi.yaml` | https://github.com/camaraproject/DeviceLocation | `r3.2` | `bc17ceeb4ee34929d5f65b8851d99d4dda4c5af1` |

Each file is `code/API_definitions/<name>.yaml` at that commit.

- **Fetched:** 2026-10-26
- **Licence:** Apache-2.0 (each repository's licence; each description's `info.license` also says Apache 2.0). The licence text is at https://www.apache.org/licenses/LICENSE-2.0.
- **Changes:** none. Each file is the upstream file byte for byte, renamed.

Why release tags: on each repository's `main` branch the descriptions refer to shared files (`../common/CAMARA_common.yaml`), and on their own fail `aram validate` with ARAM-OAS-003. The released files have those parts inlined.

SIM Swap and Number Verification are fraud signals a bank checks before releasing a payment; Quality on Demand changes the network; Device Location reveals where a person is. Many operations are POSTs that only read or verify.
