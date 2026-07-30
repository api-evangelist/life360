# Life360

Life360 is a family safety platform built around a location-sharing mobile app for iOS and Android — real-time member location, Place Alerts, location history, driving safety scores, crash detection, SOS alerts and emergency dispatch, plus digital safety features such as identity theft protection and dark web monitoring. Following the acquisitions of Tile and Jiobit, the hardware line spans Tile Mate, Pro, Slim and Sticker Bluetooth item trackers and a cellular GPS pet tracker. Membership is sold as Free, Silver, Gold and Platinum tiers.

Backed by: bessemer-venture-partners, dcm-ventures — https://www.life360.com/

## API posture

Life360 publishes **no public developer API**, no OpenAPI, no SDKs, no CLI, no webhooks and no developer portal. This was verified three ways: `developer.life360.com` / `dev.` / `developers.` / `partners.` do not resolve; there is no `life360` GitHub organization; and the Life360 help center returns zero articles for "api", "developer" or "webhook". `api.life360.com` exists but is the private mobile-app backend — the only clients for it are community reverse-engineering projects, which are not first-party artifacts and are not captured here.

What Life360 *does* publish is an **agent-facing** surface:

- [`llms.txt`](llms/life360-llms.txt) — a real, well-formed llms.txt at the site root.
- [`.well-known/ai-plugin.json`](well-known/life360-ai-plugin.json) — an OpenAI plugin manifest describing product catalog, plan and checkout capabilities. **Its `api.url` (`/openapi-spec.json`) returns 404**, so the contract it advertises does not resolve.
- [`robots.txt`](well-known/life360-robots.txt) — carries `Content-Signal: ai-train=no, ai-input=yes, search=yes` and explicit allows for GPTBot, ChatGPT-User, ClaudeBot, PerplexityBot and Google-Extended.
- [`.well-known/security.txt`](well-known/life360-security.txt) — RFC 9116, pointing at a HackerOne program and `responsibledisclosure@life360.com`. The `Expires` field is set to 2022-12-31 and is stale.

## Artifacts

| Artifact | File |
|---|---|
| Well-known index | [`well-known/life360-well-known.yml`](well-known/life360-well-known.yml) |
| security.txt | [`well-known/life360-security.txt`](well-known/life360-security.txt) |
| llms.txt | [`llms/life360-llms.txt`](llms/life360-llms.txt) |
| Domain security | [`security/life360-domain-security.yml`](security/life360-domain-security.yml) |
| Vulnerability disclosure | [`security/life360-vulnerability-disclosure.yml`](security/life360-vulnerability-disclosure.yml) |
| Conformance | [`conformance/life360-conformance.yml`](conformance/life360-conformance.yml) |
| Lifecycle | [`lifecycle/life360-lifecycle.yml`](lifecycle/life360-lifecycle.yml) |

Related network profiles: [`all/tile/`](../tile), [`all/jiobit/`](../jiobit).
