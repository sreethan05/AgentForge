<div align="center">

# AgentForge

AgentForge is a TypeScript monorepo for building AI agents, chat assistants, integrations, plugins, and bot-as-code workflows.

[Botpress Dashboard](https://app.botpress.cloud) · [Botpress CLI Reference](https://botpress.com/docs/integrations/sdk/cli-reference) · [SDK Docs](https://botpress.com/docs/integrations/sdk/overview)

</div>

## Overview

AgentForge is a developer-focused workspace for creating and deploying AI agent components. It includes examples and packages for:

- Bots-as-code: agents written and versioned in TypeScript.
- Integrations: connectors that let bots talk to external tools, APIs, and messaging platforms.
- Interfaces: contracts that integrations can implement to support common behavior.
- Plugins: reusable pieces of bot behavior that can be shared across agents.
- SDK and CLI tooling: packages that help build, validate, bundle, and deploy components.

This repository is currently based on the Botpress Cloud open-source stack. Some internal package names and dependencies still use Botpress scopes such as `@botpress/sdk`, `@botpress/client`, and `@botpress/cli`. Those names are intentionally kept because they are part of the workspace wiring.

## Tech Stack

- TypeScript
- Node.js
- pnpm workspaces
- Turbo
- Botpress SDK and CLI
- Vitest
- ESLint, Oxlint, and Prettier

## Repository Structure

| Path            | Purpose                                                                                 |
| --------------- | --------------------------------------------------------------------------------------- |
| `bots/`         | Example bots built as code.                                                             |
| `integrations/` | Connectors for services such as chat, Slack, Telegram, Google Sheets, Notion, and more. |
| `interfaces/`   | Shared contracts used by integrations and bots.                                         |
| `packages/`     | Core CLI, SDK, client, and shared packages.                                             |
| `plugins/`      | Reusable bot extensions.                                                                |
| `scripts/`      | Development and automation scripts.                                                     |
| `.github/`      | Issue templates and GitHub Actions workflows.                                           |

## Prerequisites

Install these before working with the project:

- [Git](https://git-scm.com/)
- [Node.js](https://nodejs.org/)
- [pnpm](https://pnpm.io/)
- A [Botpress Cloud](https://app.botpress.cloud) account if you want to deploy bots or integrations

## Local Setup

Clone the repository:

```sh
git clone https://github.com/sreethan05/AgentForge.git
cd AgentForge
```

Install dependencies:

```sh
pnpm install
```

Build all workspace packages:

```sh
pnpm run build
```

Run checks:

```sh
pnpm run check
```

Run formatting and lint fixes:

```sh
pnpm run fix
```

## Botpress Cloud Account Setup

Use Botpress Cloud when you want to deploy a bot, integration, interface, or plugin from this repository.

### 1. Create or Open a Botpress Account

1. Go to [https://app.botpress.cloud](https://app.botpress.cloud).
2. Sign up with your email, Google account, or the login method shown by Botpress.
3. Create a new workspace, or open an existing workspace.
4. Give the workspace a clear name, for example `AgentForge Dev`.

Your workspace is where deployed bots, integrations, and related resources will live.

### 2. Install the Botpress CLI

The Botpress CLI is used to log in, add packages, generate types, build, run locally, and deploy.

Install it globally with one of these commands:

```sh
npm install -g @botpress/cli
```

```sh
pnpm install -g @botpress/cli
```

```sh
yarn add -g @botpress/cli
```

Check that it installed correctly:

```sh
bp --help
```

### 3. Create a Personal Access Token

The CLI needs a Personal Access Token to connect your terminal to Botpress Cloud.

1. Open the [Botpress Dashboard](https://app.botpress.cloud).
2. Go to the Personal Access Tokens page.
3. Create a new token.
4. Copy it and keep it private.

Do not commit tokens, API keys, or workspace secrets to GitHub.

### 4. Find Your Workspace ID

You need your workspace ID when logging in from scripts or CI.

1. Open the [Botpress Dashboard](https://app.botpress.cloud).
2. Select your workspace.
3. Open workspace settings.
4. Copy the workspace ID or workspace handle shown there.

### 5. Log In from the CLI

Interactive login:

```sh
bp login
```

Non-interactive login:

```sh
bp login --token <your-personal-access-token> --workspace-id <your-workspace-id>
```

If you use a custom API endpoint, pass it explicitly:

```sh
bp login --token <your-token> --workspace-id <your-workspace-id> --api-url https://api.botpress.cloud
```

## Working with Bots

Bots in this repository live inside `bots/`.

Example using the hello-world bot:

```sh
cd bots/hello-world
bp add -y
bp build
bp deploy --create-new-bot
```

What these commands do:

- `bp add -y` installs the Botpress packages declared by the bot.
- `bp build` generates types and bundles the bot.
- `bp deploy --create-new-bot` creates a new bot in your Botpress workspace and deploys the code.

After deployment, open [Botpress Cloud](https://app.botpress.cloud) and check your workspace. The bot should appear in the dashboard.

To deploy to an existing bot instead of creating a new one:

```sh
bp deploy --bot-id <existing-bot-id>
```

To chat with a deployed bot from the terminal:

```sh
bp chat
```

## Adding Integrations, Interfaces, and Plugins

Use `bp add` when a bot, integration, or plugin needs another Botpress package.

Add the Chat integration:

```sh
bp add chat@latest
```

Add a messaging integration:

```sh
bp add telegram
```

Add an interface:

```sh
bp add llm --package-type interface
```

Use a local development version when working inside this monorepo:

```sh
bp add knowledge --use-dev
```

After adding packages, regenerate types:

```sh
bp gen
```

Then rebuild:

```sh
bp build
```

## Working with Integrations

Integrations live inside `integrations/`. They connect bots to external platforms such as Slack, WhatsApp, Google Sheets, Notion, Dropbox, Zendesk, and custom APIs.

Typical integration workflow:

```sh
cd integrations/<integration-name>
bp add -y
bp build
bp deploy
```

By default, deployment is private to your workspace. Use private deployments while developing so you can update and redeploy safely.

If you intentionally want to publish a public integration version:

```sh
bp deploy --visibility public
```

Only publish publicly when the integration is stable, documented, and ready for other users.

## Local Development with Botpress CLI

Run a project locally:

```sh
bp dev
```

Run on a specific port:

```sh
bp dev --port 3000
```

Pass secrets locally:

```sh
bp dev --secrets OPENAI_API_KEY=<your-key>
```

Deploy with secrets:

```sh
bp deploy --secrets OPENAI_API_KEY=<your-key>
```

Keep secrets outside Git. Prefer environment variables, Botpress Cloud configuration, or GitHub Actions secrets.

## GitHub Actions Notes

This repository includes inherited workflow files under `.github/workflows/`. Many of them are designed for a full Botpress production environment and expect secrets such as workspace IDs, tokens, and deployment credentials.

Before enabling production workflows:

- Review every workflow in `.github/workflows/`.
- Remove workflows that are not needed for AgentForge.
- Add required repository secrets in GitHub settings.
- Test deployment workflows on a small private bot or integration first.

## Common Problems

### `bp` is not recognized

The Botpress CLI is not installed or is not available in your terminal path.

```sh
npm install -g @botpress/cli
bp --help
```

### Login fails

Check that your token is valid and belongs to the selected workspace.

```sh
bp login --token <your-token> --workspace-id <your-workspace-id>
```

### Types are missing after adding an integration

Run:

```sh
bp gen
bp build
```

### Deployment creates the wrong bot

Use an explicit bot ID:

```sh
bp deploy --bot-id <existing-bot-id>
```

Use `--create-new-bot` only when you want a fresh bot in Botpress Cloud.

### GitHub Actions fail after pushing

Most failures will be caused by missing secrets or inherited workflows that are not configured for your own workspace. Disable or edit those workflows before treating CI failures as project bugs.

## Useful Links

- [Botpress Dashboard](https://app.botpress.cloud)
- [Botpress SDK Overview](https://botpress.com/docs/integrations/sdk/overview)
- [Botpress CLI Reference](https://botpress.com/docs/integrations/sdk/cli-reference)
- [Botpress Bots-as-Code Guide](https://botpress.com/docs/integrations/sdk/bots-as-code)
- [Botpress Integration Guide](https://botpress.com/docs/integrations/sdk/integration/getting-started)

## Project Status

AgentForge is in an early customization stage. The current focus is:

- Cleaning up inherited Botpress branding.
- Keeping the TypeScript workspace buildable.
- Documenting setup and cloud deployment.
- Preparing the repository for future custom agents and integrations.

## License

This project includes open-source code licensed under the MIT License. See `LICENSE` for details.
