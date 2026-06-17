# @karum/cli

Unified command-line interface for the [Karum](https://karumtek.com) commerce platform.
Binary: `karum`.

> This repository is the public home for the `@karum/cli` npm package (docs, issues,
> releases). The CLI is built from Karum's monorepo and published as a self-contained,
> zero-dependency bundle. Source for the internal packages it bundles is proprietary.

## Install

```bash
# one-off
npx @karum/cli login

# global
npm i -g @karum/cli
karum login
```

Full docs: **https://karumtek.com/developers/cli**

## Commands

### Auth & environments
| Command | Description |
| --- | --- |
| `karum login [--email <e>] [--password <p>] [--token <jwt>] [--url <baseUrl>] [--store <id>] [--profile <name>]` | Sign in with email/password (→ merchant JWT) or a direct token; stores a profile in `~/.karum/config.json`. |
| `karum whoami` | Show the active profile's identity + validate the token. |
| `karum logout [--profile <name>]` | Remove a stored profile. |
| `karum env list \| use <name> \| add <name> --url <u> --token <t> [--store <id>] \| remove <name>` | Manage named environments (prod / staging / local). |

`KARUM_API_URL` / `KARUM_API_TOKEN` / `KARUM_STORE_ID` env vars override the active profile (CI-friendly).

### Theme
`karum theme <init | validate | compile | preview | dev | pull | push | deploy> [options]` — the active profile's URL/token/store are injected automatically.

### Integration
| Command | Description |
| --- | --- |
| `karum integration scaffold [--dir <path>] [--name <name>]` | Scaffold a local integration project (`integration.json` + handlers). |
| `karum integration push --url <deliveryUrl> [--dir <path>]` | Register a webhook subscription for the manifest's topics. |
| `karum integration logs --webhook <id>` | Recent delivery attempts for a webhook. |

### Webhooks
`karum webhooks <list | topics | deliveries <id> | test <id>>` — manage tenant webhook endpoints.

## Auth model

`login` stores a **merchant JWT** (the token accepted as `Authorization: Bearer` across the
theme-packages and webhooks APIs). API keys (`sk_live_…`) authenticate via the `x-api-key`
header and are not interchangeable here.

## Issues

Bug reports and feature requests: https://github.com/karumtek/cli/issues

## License

Proprietary — see [LICENSE](./LICENSE).
