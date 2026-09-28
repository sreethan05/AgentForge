<div align="center">

# ⚒️ AgentForge

**A TypeScript monorepo for building AI agents, integrations, plugins, and bot-as-code workflows.**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=flat-square)](./LICENSE)
[![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white)](https://www.typescriptlang.org/)
[![pnpm](https://img.shields.io/badge/pnpm-10.29-F69220?style=flat-square&logo=pnpm&logoColor=white)](https://pnpm.io/)
[![Node.js](https://img.shields.io/badge/Node.js-22-339933?style=flat-square&logo=node.js&logoColor=white)](https://nodejs.org/)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen?style=flat-square)](./docs/CONTRIBUTING.md)
[![Last Commit](https://img.shields.io/github/last-commit/sreethan05/AgentForge?style=flat-square)](https://github.com/sreethan05/AgentForge/commits/main)

[Quick Start](#-quick-start) · [What's Inside](#-whats-inside) · [Integrations](#-integrations) · [Contributing](#-contributing)

</div>

---

## 🧭 Overview

**AgentForge** is a developer-first workspace for creating and deploying AI agent components — built as a [pnpm](https://pnpm.io/) monorepo orchestrated with [Turborepo](https://turbo.build/).

Instead of wiring agents together in a drag-and-drop editor, everything here is **code**: agents are written and versioned in TypeScript, integrations connect them to the outside world, and plugins package reusable behavior that can be shared across every agent in the workspace.

> **Note** — This repository is built on the [Botpress](https://github.com/botpress/botpress) open-source stack (MIT). Some internal packages still use the `@botpress/*` scope as part of the workspace wiring. Full credit and thanks to the Botpress team. 🙏

### ✨ Highlights

- 🤖 **Bots-as-code** — agents written, reviewed, and version-controlled as plain TypeScript
- 🔌 **80+ integrations** — from OpenAI and Anthropic to Slack, WhatsApp, Stripe, and Notion
- 🧩 **Reusable plugins** — knowledge bases, human-in-the-loop, analytics, personality, and more
- 🛠️ **First-class tooling** — bundled SDK, CLI, and typed API client packages
- ⚡ **Fast builds** — Turborepo task pipeline with remote caching support
- 🧪 **Quality gates** — Vitest, ESLint, Oxlint, Prettier, and Husky pre-commit hooks

---

## 🚀 Quick Start

**Prerequisites:** [Node.js 22](https://nodejs.org/) and [Git](https://git-scm.com/). pnpm is activated automatically via Corepack.

```bash
git clone https://github.com/sreethan05/AgentForge.git
cd AgentForge

corepack enable        # activates the pinned pnpm version
pnpm install           # install every workspace package

pnpm build             # build all packages (via Turborepo)
pnpm test              # run the test suite
```

Run the full quality gate before opening a PR:

```bash
pnpm check             # sherif + deps + format + lint + types
```

> 📖 More detail in [docs/SETUP.md](./docs/SETUP.md).

---

## 📦 What's Inside

| Path | Purpose |
|---|---|
| `bots/` | Example bots built as code |
| `integrations/` | **82 connectors** to external services and platforms |
| `interfaces/` | Shared contracts that integrations can implement |
| `packages/` | Core SDK, CLI, client, and supporting packages |
| `plugins/` | Reusable pieces of bot behavior |
| `scripts/` | Development and automation scripts |
| `docs/` | Setup, contributing, security, and process guides |

### Core Packages

| Package | What it does |
|---|---|
| `packages/sdk` | Type-safe SDK for building bots and integrations |
| `packages/cli` | Scaffold, build, validate, and deploy agent components |
| `packages/client` | Typed API client for the Botpress Cloud |
| `packages/chat-api` / `chat-client` | Embeddable chat widget API and client |
| `packages/common` | Shared utilities used across the workspace |
| `packages/cognitive` | LLM orchestration primitives (prompts, tools) |
| `packages/llmz` | Tool-calling engine for LLM programs |
| `packages/vai` · `zai` · `zui` · `sdk-addons` | Supporting packages |

---

## 🔌 Integrations

Every connector lives in `integrations/` as its own package. A few examples:

<p>
  <img alt="OpenAI" src="https://img.shields.io/badge/OpenAI-412991?style=flat-square&logo=openai&logoColor=white" />
  <img alt="Anthropic" src="https://img.shields.io/badge/Anthropic-191919?style=flat-square&logo=anthropic&logoColor=white" />
  <img alt="Slack" src="https://img.shields.io/badge/Slack-4A154B?style=flat-square&logo=slack&logoColor=white" />
  <img alt="Telegram" src="https://img.shields.io/badge/Telegram-26A5E4?style=flat-square&logo=telegram&logoColor=white" />
  <img alt="WhatsApp" src="https://img.shields.io/badge/WhatsApp-25D366?style=flat-square&logo=whatsapp&logoColor=white" />
  <img alt="Notion" src="https://img.shields.io/badge/Notion-000000?style=flat-square&logo=notion&logoColor=white" />
  <img alt="GitHub" src="https://img.shields.io/badge/GitHub-181717?style=flat-square&logo=github&logoColor=white" />
  <img alt="Stripe" src="https://img.shields.io/badge/Stripe-635BFF?style=flat-square&logo=stripe&logoColor=white" />
  <img alt="Google Calendar" src="https://img.shields.io/badge/Google_Calendar-4285F4?style=flat-square&logo=googlecalendar&logoColor=white" />
  <img alt="Linear" src="https://img.shields.io/badge/Linear-5E6AD2?style=flat-square&logo=linear&logoColor=white" />
</p>

<details>
<summary><strong>📜 View all 82 integrations</strong></summary>

| Category | Integrations |
|---|---|
| 🤖 **AI & LLM** | anthropic, cerebras, dalle, fireworks-ai, google-ai, groq, mistral-ai, openai |
| 💬 **Messaging** | chat, freshchat, instagram, intercom, kommo, line, messenger, sunco, teams, telegram, twilio, viber, vonage, wechat, whatsapp, zendesk-messaging-hitl |
| 📧 **Email** | email, gmail, hunter, loops, mailchimp, postmark, resend, sendgrid |
| 📋 **Productivity** | airtable, asana, attio, canny, charts, clickup, confluence, feature-base, gsheets, jira, linear, mintlify, monday, notion, tally, trello, todoist |
| 🛠️ **Dev & Automation** | browser, github, make, n8n, pdf-generator, webhook, zapier |
| 💼 **CRM & HR** | bamboohr, hubspot, linkedin, odoo, salesforce, workable, zoho |
| 🛍️ **Commerce** | bigcommerce-sync, shopify-admin, shopify-storefront, stripe, webflow |
| 📅 **Scheduling & Docs** | calcom, calendly, docusign, googlecalendar, zoom |
| ☁️ **Files & Storage** | dropbox, googledrive, googledrivekb, sharepoint |
| 🆘 **Support & Analytics** | freshdesk, google-analytics, zendesk |

</details>

### 🧩 Plugins

`analytics` · `conversation-insights` · `file-synchronizer` · `hitl` (human-in-the-loop) · `knowledge` · `knowledge-connector` · `logger` · `personality` · `synchronizer`

---

## 🧰 Useful Scripts

| Command | Description |
|---|---|
| `pnpm build` | Build all packages via Turborepo |
| `pnpm test` | Run the full test suite |
| `pnpm check` | Everything: sherif, deps, format, lint, and types |
| `pnpm fix` | Auto-fix dependency rules, format, and lint issues |
| `pnpm check:type` | TypeScript type-check across the workspace |

<details>
<summary><strong>All commands</strong></summary>

| Command | Description |
|---|---|
| `pnpm bump` | Bump workspace dependency versions |
| `pnpm check:bplint` | Lint bot definitions |
| `pnpm check:dep` | Check dependency rules (depsynky) |
| `pnpm check:sherif` | Check monorepo lint rules (sherif) |
| `pnpm check:format` | Check code formatting (Prettier) |
| `pnpm check:eslint` | Lint with ESLint (zero warnings) |
| `pnpm check:oxlint` | Lint with Oxlint |
| `pnpm check:lint` | bplint + oxlint + eslint |
| `pnpm fix:dep` | Sync dependency versions |
| `pnpm fix:format` | Format the codebase |
| `pnpm fix:oxlint` | Fix Oxlint issues |
| `pnpm fix:eslint` | Fix ESLint issues |

</details>

---

## 📚 Documentation

- [Setup Guide](./docs/SETUP.md) — local environment from zero
- [Contributing Guide](./docs/CONTRIBUTING.md) — how to open a good PR
- [Code of Conduct](./docs/CODE_OF_CONDUCT.md) — community standards
- [Security Policy](./docs/SECURITY.md) — how to report vulnerabilities
- [Git Workflow](./docs/GIT_WORKFLOW.md) — branching and commit conventions
- [Release Process](./docs/RELEASE_PROCESS.md) — how releases are cut
- [FAQ](./docs/FAQ.md) — common questions

---

## 🤝 Contributing

Contributions are welcome! 🎉

1. 🍴 Fork the repository
2. 🌿 Create a branch: `git checkout -b feat/my-feature`
3. 💾 Commit your changes with a clear message
4. ✅ Make sure `pnpm check` and `pnpm test` pass
5. 🔃 Open a pull request against `main`

Please read [docs/CONTRIBUTING.md](./docs/CONTRIBUTING.md) first — bug reports and feature requests go through the [issue templates](./.github/ISSUE_TEMPLATE).

## ⭐ Show Your Support

If you find this project useful, please consider giving it a ⭐ — it helps others discover it!

## 🙏 Acknowledgments

Built on the shoulders of the [Botpress](https://github.com/botpress/botpress) open-source stack. Check out their work — it's excellent.

## 📄 License

Distributed under the [MIT License](./LICENSE).

---

<div align="center">

**Made with ⚒️ by [sreethan05](https://github.com/sreethan05)**

</div>
