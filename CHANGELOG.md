# Changelog

## 0.4.2

- `repository` metadata now points to this public repo (`darastr/cli`); `homepage` points
  to https://developers.daras.com.tr.

## 0.4.1

- Metadata-only release while the public home moved.

## 0.4.0

- Package renamed from `@karum/cli` to `@darastr/cli` as part of the Daras rebrand; the
  old package is deprecated on npm with a pointer here. Binary renamed to `daras`.
- Theme toolkit: publish-gate linting now validates the Daras Reactive Engine expression
  language (`daras-state/text/show/class/model/computed/persist/on:*`) and the safe
  `json` filter; `daras theme docs` documents the full surface.
- Partner app commands (`daras app …`): scaffold, local dev loop, versioned deploys.

## 0.1.1

- First public release on npm (as `@karum/cli`).

## 0.1.0

- Initial build: `auth` (login/whoami/logout/env), `theme` (delegated to the theme
  toolkit), `integration` (scaffold/push/logs), `webhooks` (list/topics/deliveries/test).
