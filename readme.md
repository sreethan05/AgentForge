<div align="center">

# AgentForge

AgentForge is a TypeScript monorepo for building AI agents, chat assistants, integrations, plugins, and bot-as-code workflows.

</div>

## Overview

AgentForge provides a workspace for experimenting with production-style agent tooling. It includes examples for bots, integrations, plugin development, SDK/client packages, and automation-oriented development scripts.

This project is currently based on the Botpress Cloud open-source stack, so some internal package names and dependencies still use Botpress scopes such as `@botpress/sdk`, `@botpress/client`, and `@botpress/cli`. Those package scopes are intentionally kept intact so the workspace can continue to build correctly.

## Repository Structure

- `bots/` - example bots built as code.
- `integrations/` - integration packages for connecting agents to external services.
- `interfaces/` - interface packages used by the workspace.
- `packages/` - core CLI, SDK, client, and shared tooling packages.
- `plugins/` - plugin packages for extending agent behavior.
- `scripts/` - development and automation scripts.

## Local Development

### Prerequisites

- Git
- Node.js
- pnpm

### Setup

```sh
pnpm install
```

### Build

```sh
pnpm run build
```

### Run Checks

```sh
pnpm run check
```

## Project Status

AgentForge is in an early customization stage. The current focus is rebranding the workspace, cleaning up inherited project metadata, and preparing the repository for GitHub.

## License

This project includes open-source code licensed under the MIT License. See `LICENSE` for details.
