# 🛸 RHmachine — beta 2.1.0-beta.2

Local market radar · Apple Silicon macOS · terminal interface

[Keyboard controls](https://github.com/sdb001/RHmachine-setup/blob/main/KEYBOARD.md) · [Setup](https://github.com/sdb001/RHmachine-setup/blob/main/SETUP.md)

## New in beta.2

- Long discovery checks missing contracts for priced, liquid, traded markets within the existing quote-request budget.
- Busier Long ecosystem markets retain a refresh rotation through quiet five-minute windows. Long and Split use SUSTAINED FIRST ordering; activity is not proof of safety.
- Optional HyperSync historical-label repair verifies older exact-contract launch events against RPC, saves progress, and honours hidden coins. Coverage is gradual and limited to recognized Long factories.
- Split adds VOL SIG multipliers and cyan spike arrows, plus a pink selection outline that follows the focused pane without covering data colours.

This is an unsigned test build. It has no Apple Developer ID signature or notarization. macOS may block it. If that happens, stop and report the message; these instructions do not disable Gatekeeper or remove quarantine protections.

The compiled app runs locally without Node.js or Bun installed. Python 3 is required; its state-lock helper uses macOS file locking. Hermes is optional and needs its own model login. Chart image generation also requires Hermes's Python plotting dependencies.

## Install

1. Verify the archive against the SHA256SUMS file received with it. This detects corruption; it does not authenticate an unsigned publisher.
2. Extract the archive and open Terminal in its extracted folder.
3. Run `sh install.sh`. It verifies package contents and refuses to replace an existing RHmachine command or version.
4. Run `~/.local/bin/rhmachine setup`.
5. Run `~/.local/bin/rhmachine terminal`.

If ~/.local/bin is on your shell PATH, `rhmachine` works directly. Otherwise use the full command above.

## Upgrade from beta.1

Quit RHmachine and back up ~/.rhmachine before upgrading. Verify and extract the new archive, then run `sh install.sh --upgrade` from its folder. This accepts only the original beta.1 launcher symlink, keeps the old version's files, and switches the launcher to beta.2. It does not overwrite other installations or modify your data, credentials or AI profile. Launch with `~/.local/bin/rhmachine terminal`; no fresh setup is required.

If your Hermes/MCP configuration uses a version-specific binary path, reconnect it to beta.2 using CONNECT.md and restart the affected client/gateway. For an existing dedicated Hermes profile, `~/.local/bin/rhmachine connect hermes PROFILE_NAME` preserves its existing model and other settings. Other MCP clients can use `~/.local/bin/rhmachine connect mcp` to obtain the new configuration.

## API setup

Public Robinhood RPC, DexScreener and GeckoTerminal endpoints are built in. They remain subject to provider limits and availability. No shared private keys are bundled. The setup wizard optionally accepts a private HTTPS RPC URL, Nansen key, HyperSync token, X bearer token and Bubblemaps key. Input is hidden, blank preserves an existing value, and values stay in the local .env with owner-only permissions.

Adding Nansen enables its scheduled snapshots within the configured daily cap (50 credits by default). X and other research services may consume the customer’s credits when used. Saved credentials are not automatically validated. API errors and unsupported coverage remain visible rather than being treated as successful checks.

## AI

Start without AI, or follow CONNECT.md. Automatic AI is off by default; REVIEW queues alerts for manual analysis. Provider/API usage belongs to the customer's accounts. Setup does not copy the developer's identity, credentials, wallets or memories.

The dashboard `i` key uses the Hermes bridge. Other MCP clients can research and save reviews via tools; adding an MCP server alone does not connect that key. The first authenticated report is a beta acceptance check and may consume AI usage.

## Data and removal

Local configuration and history: ~/.rhmachine. Installed files: ~/.local/share/rhmachine/2.1.0-beta.2. Launcher: ~/.local/bin/rhmachine.

Quit RHmachine before removing files. To uninstall, verify the launcher points to this beta, remove that symlink and this version's installed directory. Keep ~/.rhmachine and your Hermes profile to preserve data. Updates are explicit; the installer refuses existing commands unless the recognized beta.1 upgrade is requested.

## Scope

The app's source repository is private. This download contains the executable and support resources, not a source checkout. Applicable third-party licences are retained under resources. This is a evaluation build, not a public stable release or a guarantee of trading outcomes. No private signing module is included.

Report the app version, macOS version and the action that failed. Do not include API secrets, private keys or seed phrases in a bug report.
