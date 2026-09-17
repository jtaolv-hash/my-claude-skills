---
name: agent-reach
description: >
  Install, configure, diagnose, and use Agent-Reach — a CLI that gives an AI agent
  read access to web pages, YouTube, GitHub, RSS, Bilibili, Twitter/X, Reddit,
  LinkedIn, 小红书, 雪球, 小宇宙, V2EX, Boss直聘, and similar platforms.
  Trigger on: "agent-reach", "agent reach", "install agent-reach", "agent-reach
  install", "agent-reach doctor", "give Claude internet access", "give my agent
  web access", "scrape Twitter for me", "read this Xiaohongshu post",
  "add a platform channel", "why is agent-reach failing".
  CRITICAL: the upstream README's `pip install agent-reach` command is WRONG and
  installs an unrelated package — always install from the GitHub archive.
  Default to core channels only; treat cookie-based channels as a credential risk
  and never enable one without explicit per-channel user approval.
---

# Agent-Reach

Agent-Reach is a selector, installer, and health checker for upstream tools that
give an agent internet reach. It is not a scraper itself — it installs and wires up
other people's connectors, then exposes them behind one CLI with a consistent
response envelope. It keeps all state in `~/.agent-reach/` and never in the workspace.

Upstream: https://github.com/Panniantong/Agent-Reach

---

## Step 0 — Resolve which `agent-reach` is meant

Three unrelated projects share this name. Confirm before installing anything.

| Where | Who | What it is | Is it the one? |
|---|---|---|---|
| `github.com/Panniantong/Agent-Reach` | Panniantong | Multi-platform connector installer, `agent-reach install` / `doctor` | **Yes — this skill covers this one** |
| PyPI `agent-reach` (0.1.0) | Jean Galea (`github.com/jgalea/agent-reach`) | Different design: per-channel TOML manifests, token budgeting | No |
| npm `agent-reach` (0.3.4) | AustinEral | Nostr / OpenClaw agent network plugin; **deprecated** | No |

**The trap:** Panniantong's README instructs `pip install agent-reach`. That PyPI name
belongs to Jean Galea's unrelated project. Running the README command installs a
stranger's alpha package, not Agent-Reach. Panniantong's own `docs/install.md`
installs from the GitHub archive — that is the authoritative path. Use it.

If the user asks for the Jean Galea or npm project instead, stop and use their docs;
nothing below applies.

---

## Step 1 — Check the environment is worth installing into

Agent-Reach stores everything in `~/.agent-reach/` and depends on persistent browser
login sessions. **Do not install it in an ephemeral container** (Claude Code on the
web, CI runners, throwaway VMs) — the state is destroyed on teardown and the
credentialed channels cannot authenticate. If the current environment is ephemeral,
say so and tell the user to run the install on their own machine.

Prerequisites to verify first:

```bash
python3 --version        # needs 3.10+
which pipx node gh       # Node.js and gh CLI are used by several channels
```

---

## Step 2 — Install (GitHub archive, never PyPI)

Preferred, with pipx:

```bash
pipx install https://github.com/Panniantong/agent-reach/archive/main.zip
```

If pipx is unavailable or you hit a PEP 668 "externally managed environment" error,
use a dedicated venv:

```bash
python3 -m venv ~/.agent-reach-venv
source ~/.agent-reach-venv/bin/activate
pip install https://github.com/Panniantong/agent-reach/archive/main.zip
```

Windows PowerShell:

```powershell
py -3 -m venv $env:USERPROFILE\.agent-reach-venv
$env:USERPROFILE\.agent-reach-venv\Scripts\Activate.ps1
python -m pip install https://github.com/Panniantong/agent-reach/archive/main.zip
```

---

## Step 3 — Check-only pass, then approved system pass

Never run the `--system` pass before showing the user what the check-only pass wants
to change.

```bash
agent-reach install --env=auto            # read-only: reports gaps, modifies nothing
```

Show the output. Then, only after explicit approval:

```bash
agent-reach install --env=auto --system   # installs deps, activates core channels
```

The `--system` pass installs missing system dependencies (Node.js, `gh`, `mcporter`)
and Python deps, and activates the core channels: web search, YouTube, GitHub, RSS,
Exa Search, V2EX, and basic Bilibili. These need no credentials.

---

## Step 4 — Optional channels (opt-in, one at a time)

```bash
agent-reach install --env=auto --system --channels=opencli,twitter
```

Available beyond core: OpenCLI, Twitter, Xueqiu (雪球), Xiaoyuzhou (小宇宙),
XiaoHongShu (小红书), Reddit, Facebook, Instagram, full Bilibili, LinkedIn, Boss直聘.

**Default to core only.** Do not add a credentialed channel unless the user names it.
See the credential-risk section below before enabling any of them.

---

## Step 5 — Configure credentials per channel

| Channel | Method |
|---|---|
| Twitter/X | Cookie-Editor export of auth tokens |
| XiaoHongShu | OpenCLI (desktop) or Cookie-Editor export for CLI tools |
| Xueqiu | `agent-reach configure --from-browser chrome --platform xueqiu` |
| Xiaoyuzhou | Free Groq API key: `agent-reach configure groq-key` |
| Reddit / Facebook / Instagram | Browser login session via OpenCLI |
| Boss直聘 | Desktop only; manual Chrome login with CDP debugging enabled |

---

## Step 6 — Diagnose

```bash
agent-reach doctor
```

Run this after every install or configure step. It reports what is missing or broken
per channel. Surface its output to the user verbatim rather than summarizing away
failures — a silently degraded channel returns empty results that look like "no data"
rather than "not authenticated".

---

## Credential risk — read before enabling cookie-based channels

The credentialed channels work by exporting **live session cookies** from the user's
browser and handing them to a third-party CLI, which then holds persistent
authenticated access to those accounts until the session expires. That is a real
blast radius on a machine that also runs brokerage, trading, or finance tooling, in
exchange for what is mostly read-only scraping.

Default recommendation: core channels plus Exa semantic search. That covers most of
the practical value with zero credential exposure. Enable a cookie-based channel only
when the user asks for that specific platform, and say plainly what is being handed
over. This is a trade-off to state, not a decision to make silently for the user.

---

## Operational boundaries (enforced by upstream docs)

- Never run `sudo` without explicit user permission.
- Never modify files outside `~/.agent-reach/`.
- Never clone repos or create files in the user's workspace — tool repos belong in
  `~/.agent-reach/tools/`, configs in `~/.agent-reach/`.
- Never disable security features to make a channel work.

---

## Troubleshooting

**`agent-reach: command not found` after install** — the venv is not active. Either
`source ~/.agent-reach-venv/bin/activate` or call the absolute path
`~/.agent-reach-venv/bin/agent-reach`. pipx installs put it on PATH automatically.

**PEP 668 / externally-managed-environment** — use the venv path in Step 2. Do not
pass `--break-system-packages`.

**A channel returns empty results** — run `agent-reach doctor` before assuming the
platform has no data. Expired cookies fail silently as empty responses.

**Install appears to do nothing** — `--env=auto` alone is check-only by design. The
`--system` flag is what actually changes the machine.

**Sandbox or proxy blocks the install** — installing from a GitHub archive executes
third-party code and is blocked in some managed environments. That is a correct
refusal, not a bug; run the install on a machine the user controls.

---

## Verification note

Install commands, channel lists, and credential methods above were read from
upstream `docs/install.md` and `README.md` on 2026-09-17. Upstream is an actively
moving project. If a documented command fails, re-read
https://raw.githubusercontent.com/Panniantong/agent-reach/main/docs/install.md
before improvising, and prefer whatever that file says over this skill.
