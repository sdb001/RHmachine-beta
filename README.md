# 🛸 RHmachine — beta 2.1.0-beta.1

Local market radar · Apple Silicon macOS · terminal interface

[Download the compiled beta](https://github.com/sdb001/RHmachine-beta/releases/tag/v2.1.0-beta.1) · [AI-assisted setup instructions](https://github.com/sdb001/RHmachine-setup/blob/main/SETUP.md)

Downloads are public; application source remains private. No GitHub invitation is required. Choose the named macOS archive, not GitHub's automatic “Source code” downloads, which contain only this repository's documentation.

This is an unsigned test build. It has no Apple Developer ID signature or notarization. macOS may block it. If that happens, stop and report the message; these instructions do not disable Gatekeeper or remove quarantine protections.

The compiled app runs locally without Node.js or Bun installed. Python 3 is required; its state-lock helper uses macOS file locking. Hermes is optional and needs its own model login. Chart image generation also requires Hermes's Python plotting dependencies.

## Install

1. Verify the archive against the SHA256SUMS file received with it. This detects corruption; it does not authenticate an unsigned publisher.
2. Extract the archive and open Terminal in its extracted folder.
3. Run `sh install.sh`. It verifies package contents and refuses to replace an existing RHmachine command or version.
4. Run `~/.local/bin/rhmachine setup`.
5. Run `~/.local/bin/rhmachine terminal`.

If ~/.local/bin is on your shell PATH, `rhmachine` works directly. Otherwise use the full command above.

## API setup

Public Robinhood RPC, DexScreener and GeckoTerminal endpoints are built in. They remain subject to provider limits and availability. No shared private keys are bundled. The setup wizard optionally accepts a private HTTPS RPC URL, Nansen key, HyperSync token, X bearer token and Bubblemaps key. Input is hidden, blank preserves an existing value, and values stay in the local .env with owner-only permissions.

Adding Nansen enables its scheduled snapshots within the configured daily cap (50 credits by default). X and other research services may consume the customer’s credits when used. Saved credentials are not automatically validated. API errors and unsupported coverage remain visible rather than being treated as successful checks.

## AI

Start without AI, or follow CONNECT.md. Automatic AI is off by default; REVIEW queues alerts for manual analysis. Provider/API usage belongs to the customer's accounts. Setup does not copy the developer's identity, credentials, wallets or memories.

The dashboard `i` key uses the Hermes bridge. Other MCP clients can research and save reviews via tools; adding an MCP server alone does not connect that key. The first authenticated report is a beta acceptance check and may consume AI usage.

## Data and removal

Local configuration and history: ~/.rhmachine. Installed files: ~/.local/share/rhmachine/2.1.0-beta.1. Launcher: ~/.local/bin/rhmachine.

Quit RHmachine before removing files. To uninstall, verify the launcher points to this beta, remove that symlink and this version's installed directory. Keep ~/.rhmachine and your Hermes profile to preserve data. There is no automatic update or data migration in this beta; the installer stops if an existing installation is found.

## Scope

The app's source repository is private. This download contains the executable and support resources, not a source checkout. Applicable third-party licences are retained under resources. This is an evaluation build, not a stable release or a guarantee of trading outcomes. No private signing module is included. The original archive and included documentation still call this a “private beta”; public download availability has changed, and its checksummed contents are unchanged.

Report the app version, macOS version and the action that failed. Do not include API secrets, private keys or seed phrases in a bug report.
