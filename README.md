<div align="center">

# brainforge

> A forge for Claude Code skills — crafted and actually used.

[![Claude Code](https://img.shields.io/badge/Claude%20Code-Marketplace-blueviolet)](https://claude.ai/code)
[![Plugins](https://img.shields.io/badge/plugins-3-green)](#whats-inside)
[![Status](https://img.shields.io/badge/status-v0.1.3-orange)](#)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

A Claude Code plugin marketplace.
Aggregates skills and plugins I've written and actually use, so others can install them with a single command.

[Install](#install) · [What's Inside](#whats-inside) · [Contribute](#contribute--feedback) · [Changelog](CHANGELOG.md) · [Releases](https://github.com/zning1994/brainforge/releases)

**Other Languages / 其他语言：**

[简体中文](README_CN.md) · [日本語](README_JA.md) · [Español](README_ES.md) · [Deutsch](README_DE.md) · [한국어](README_KO.md) · [Português](README_PT.md) · [Русский](README_RU.md)

</div>

---

## What This Is

brainforge is not a single skill — it is a **manifest repository**. It contains just a `marketplace.json` that lists each plugin's own GitHub repo. Claude Code reads this manifest and pulls each skill from its source repo.

Every skill has its own repo, its own issue tracker, and its own release cadence. brainforge is the shelf that holds them all in one place.

---

## Install

### Add the marketplace

```bash
/plugin marketplace add zning1994/brainforge
```

### Install a plugin

```bash
/plugin install cooking-skill@brainforge
/plugin install docs-organization@brainforge
/plugin install brainforge-autoresearch@brainforge
```

### Update to the latest

```bash
/plugin marketplace update brainforge
/reload-plugins
```

---

## What's Inside

### cooking-skill

Helps you decide what to cook tonight, how to cook it, and how to save a dish when something goes wrong. Defaults to Chinese home cooking, asks two sharp questions before recommending, and gives you something you can actually put in a pan.

- Repo: [zning1994/cooking-skill](https://github.com/zning1994/cooking-skill)
- Triggers on: `what should I cook tonight`, `I have X and Y, what can I make`, `how do I stir-fry beef so it stays tender`

### docs-organization

Organizes project documentation by size, audience, and freshness. Slims bloated CLAUDE.md / AGENTS.md files, decides where each doc should live, and prevents duplicate facts from spreading across your repo.

- Repo: [zning1994/docs-organization](https://github.com/zning1994/docs-organization)
- Triggers on: new project doc scaffolding, CLAUDE.md over 250 lines, messy docs needing a restructure

### brainforge-autoresearch

Automatically optimizes a skill's prompt. Inspired by Karpathy's autoresearch pattern: define binary evals, let an agent loop run experiments, mutate the prompt, and keep the better variants.

- Repo: [zning1994/brainforge-autoresearch](https://github.com/zning1994/brainforge-autoresearch) (formerly `openclaw-autoresearch`)
- Triggers on: a skill that isn't working well and needs systematic tuning, comparing multiple prompt variants

---

## Project Structure

```text
brainforge/
├── .claude-plugin/
│   └── marketplace.json    # Plugin catalog (points at each source repo)
├── README.md               # This file (English, default)
├── README_CN.md            # Chinese version
├── CHANGELOG.md
└── LICENSE
```

Each plugin entry in `marketplace.json` uses `source.url` to point at its own repo. brainforge stays lightweight — when a skill updates, just push to its source repo. brainforge only changes when you add/remove a plugin or update the catalog metadata.

---

## Design Principles

- **One skill, one repo** — independent versioning, independent issues, independent releases
- **brainforge is just a catalog** — no content duplication, only aggregation
- **OpenClaw / ClawHub coexistence** — the same skill can be published to both
- **One change, one place** — updating the URL in `marketplace.json` doesn't touch the skill itself

---

## Contribute / Feedback

- Problem with a specific skill → file an issue on that skill's repo
- Problem with the marketplace itself (wrong URL, missing entry) → file an issue on this repo
- Want to publish your own skills this way → fork this repo as a template for your own marketplace

---

## License

[MIT](LICENSE)
