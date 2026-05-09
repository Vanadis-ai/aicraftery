# AI Craftery

> Workspace tool for layered AI-native development.
> One desktop app, every AI coding agent that matters, your sessions and your files in one place.

[**aicraftery.com**](https://aicraftery.com) · [**install**](#install) · [**features**](#what-it-does) · [**releases**](https://github.com/Vanadis-ai/aicraftery/releases)

---

## What it is

AI Craftery is a desktop workspace where you talk to your coding agents the way you talk to your editor: long-running sessions, file context, terminals, multi-agent tabs side by side. The current surface is **AI Craftery Bord** — the macOS / Linux desktop client.

The product line is named for the Old Norse *vedissa* (a knower / keeper of context). You craft. The tools remember.

## What it does

- **Multi-agent tabs.** Claude Code, Codex, Gemini CLI — one window, one session list.
- **Long-running sessions.** Browse, search, resume, rename, delete. Switch context without losing thread.
- **Streaming.** Real-time text, thinking, tool use, permission prompts — no polling, no refresh.
- **Files in context.** Drag a file onto a session, the agent gets the path. Open files inline; preview images / PDFs / CSV.
- **Terminals.** First-class terminal panels that share the workspace with the chat — no alt-tab.
- **Editor.** Edit text and code right in the workspace; save from the same window where the agent is reading the file.
- **Telegram bots.** Per-agent bots with configurable models and permissions; talk to your sessions from your phone.
- **Assistants.** Reusable templates with custom system prompts and tool sets; switch personas without re-typing the brief.
- **Client-server split.** Desktop connects to the local Go daemon (or a remote one) over HTTP/WebSocket. Daemon survives the window close — Telegram bots and remote clients keep working.
- **Service mode.** Daemon registers as a launchd / systemd user service with auto-respawn — close the app, the daemon stays. Crash, the supervisor brings it back.
- **Remote pairing.** Pair another machine with a one-time code; drive sessions running elsewhere.
- **4 themes.** Dark, Light, Dark Blue, Dark Sand.

## Install

**macOS** (Apple-signed, notarized):
```
curl -fsSL https://releases.aicraftery.com/install-mac.sh | bash
```

**Linux** (Ubuntu / Debian / Fedora / Arch / openSUSE):
```
curl -fsSL https://releases.aicraftery.com/install-linux.sh | bash
```

Or grab the platform installer from [Releases](https://github.com/Vanadis-ai/aicraftery/releases) directly:
- `aicraftery-bord-vX.Y.Z-macos-arm64.pkg` — Apple Installer
- `aicraftery-bord-vX.Y.Z-macos-arm64.zip` — bundle .app for manual drop into `~/Applications`
- `aicraftery-bord-vX.Y.Z-linux-amd64.deb` — Debian / Ubuntu
- `AI-Craftery-Bord-vX.Y.Z-linux-x86_64.AppImage` — distribution-agnostic
- `aicraftery-bord-vX.Y.Z-linux-amd64.tar.gz` — manual extract

Both install scripts:
- land the bundle in **`~/Applications`** (no `sudo` for the app itself)
- install the Go daemon as a **launchd** (macOS) / **systemd `--user`** (Linux) service with `KeepAlive=true` / `Restart=always` — auto-respawn on any unexpected exit
- write daemon stderr to `~/.Vanadis/aicraftery-bord-server.err.log` for diagnostics

## Linux headless (server-only)

If you want the daemon without the desktop, install just the server binary:

```
curl -LO https://github.com/Vanadis-ai/aicraftery/releases/latest/download/aicraftery-bord-server-vX.Y.Z-linux-amd64.tar.gz
tar xzf aicraftery-bord-server-*-linux-amd64.tar.gz
./aicraftery-bord-server server install
./aicraftery-bord-server server start
```

Connect to it from a desktop on another machine via the remote-pairing flow.

## Requirements

At least one AI CLI tool installed and configured:

- [Claude Code](https://docs.anthropic.com/en/docs/claude-code) — Anthropic
- [Codex](https://github.com/openai/codex) — OpenAI
- [Gemini CLI](https://github.com/google/gemini-cli) — Google

## What this repo is

This is the **public release mirror** for AI Craftery Bord — release artifacts (`.pkg`, `.zip`, `.deb`, `.AppImage`, `.tar.gz`), checksums, and signed update manifests consumed by the in-app updater.

Source code lives in a separate private repository. Issues and feature requests welcome on this repo's [Issues tab](https://github.com/Vanadis-ai/aicraftery/issues).

## License

AI Craftery Bord is **free to use** — closed freeware. Binaries are signed and notarized; you keep using whatever AI CLI you already pay for / run for free, AI Craftery does not add a layer between your CLI and its provider.

## Links

- [aicraftery.com](https://aicraftery.com) — product site
- [Releases](https://github.com/Vanadis-ai/aicraftery/releases) — every version
- [Issues](https://github.com/Vanadis-ai/aicraftery/issues) — bug reports and feature requests
- [Vanadis](https://vanadis.ai) — the brand
- [vanadis-open-bord](https://github.com/Vanadis-ai/vanadis-open-bord) — sister open-source projects (`amail` cross-agent mailbox + Claude Code marketplace plugins)

---

*Previously known as Vedissa Bord (releases.vedissa.com). The product is the same; the name is sharper.*
