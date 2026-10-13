# base_desktop

Desktop (Tauri 2) shell for the **Base** POS. It renders the `biggie_pos` frontend
(`../biggie_pos`) and talks to the `biggie_api` backend — the frontend is not
duplicated here, so every change in `biggie_pos` is automatically in the desktop app.

## Requirements

- Node.js + pnpm
- Rust toolchain (cargo)
- `biggie_pos` checked out next to this folder, with dependencies installed
  (`pnpm install`)
- `biggie_api` running (default `http://localhost:3002`)

## Development

```sh
pnpm install
pnpm desktop:dev
```

Starts the vite dev server in `../biggie_pos` (port 5374) and opens the app window.

## Runtime settings

On the login screen, click the gear icon (top-right) to set:

- **POS API URL** — e.g. `http://localhost:3002` (local biggie_api) or the hosted API
- **Tenant/admin API URL** — defaults to `https://api.admin.reliatech.co.ke`
- **Zoom** — also `Ctrl` + `+` / `-` / `0`

## Build installer

```sh
pnpm desktop:build
```

Produces a Windows installer in `src-tauri/target/release/bundle/`:
`nsis/Base_<version>_x64-setup.exe`.

Bump the version in all three places: `package.json`, `src-tauri/tauri.conf.json`,
`src-tauri/Cargo.toml`.
