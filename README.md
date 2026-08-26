# @darastr/cli

Unified command-line interface for the [Daras](https://daras.com.tr) commerce platform.
Binary: `daras`.

> This repository is the public home for the `@darastr/cli` npm package (docs, issues,
> releases). The CLI is built from Daras's monorepo and published as a self-contained
> bundle. Source for the internal packages it bundles is proprietary.
>
> `@karum/cli` was the previous name of this package; it is deprecated on npm and all
> releases continue here under the `@darastr` scope.

## Install

```bash
# one-off
npx @darastr/cli login

# global
npm i -g @darastr/cli
daras login
```

Full docs: **https://developers.daras.com.tr**

## Commands

### Auth & environments
| Command | Description |
| --- | --- |
| `daras login [--url <baseUrl>] [--store <id>] [--profile <name>]` | Browser-authorize (opens the panel; approve to store a profile). |
| `daras login --token <jwt>` / `--email <e> --password <p>` | Non-interactive login (CI / scripts). |
| `daras whoami` | Show the active profile's identity + validate the token. |
| `daras logout [--profile <name>]` / `daras logout --all` | Remove one or every stored profile. |
| `daras env list \| use <name> \| add <name> --url <u> --token <t> [--store <id>] \| remove <name>` | Manage named profiles. |

`DARAS_API_URL` / `DARAS_API_TOKEN` / `DARAS_STORE_ID` env vars override the active profile (CI-friendly).

### Theme
`daras theme <init | validate | compile | dev | pull | push | deploy> [options]` — the full
theme toolkit (Liquid engine, publish-gate linting including the reactive expression
language, live preview) using the active profile. `daras theme docs` prints the complete
theme-language reference.

### Integration
| Command | Description |
| --- | --- |
| `daras integration scaffold [--dir <path>] [--name <name>]` | Scaffold a local integration project. |
| `daras integration push --url <deliveryUrl> [--dir <path>]` | Register the manifest's webhook topics. |
| `daras integration logs --webhook <id>` | Recent delivery attempts for a webhook. |

### Webhooks
`daras webhooks <list | topics | deliveries <id> | test <id>>` — manage tenant webhook endpoints.

### Apps (partner)
`daras app <list | create | info | init | env | rotate-secret | open | scaffold | generate extension | dev | deploy | versions>` —
build, run and ship embedded partner apps (OAuth clients, local dev loop with tunnel,
versioned deploys into review).

## Auth model

`login` stores a **merchant JWT** (the token accepted as `Authorization: Bearer` across the
theme-packages and webhooks APIs). API keys (`sk_live_…`) authenticate via the `x-api-key`
header and are not interchangeable here.

## Issues

Bug reports and feature requests: https://github.com/darastr/cli/issues

## License

Proprietary — see [LICENSE](./LICENSE).
