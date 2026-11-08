# DDGS MCP

This repository packages the upstream DDGS web search and content extraction MCP server for Claude Code and Codex.
It contains no search implementation of its own.
The plugin declares the server configuration and installs the published `ddgs` package at launch.

## Runtime

The server runs over stdio through `uvx`.
The `ddgs[mcp]` requirement installs the optional dependencies the MCP server needs.
The `--with pip-system-certs` option adds operating system certificate support to the same tool environment.
The runtime requires `uv` and a Python version supported by the upstream package.
`uvx` reuses its ephemeral tool environment in the default uv cache between launches.
Run `uv cache clean` when you want uv to resolve the package again.

## Install

Install the plugin from the Sinon marketplace in Claude Code:

```sh
claude plugin marketplace add ririnto/sinon
claude plugin install ddgs-plugin@sinon
```

For local development, load the package in a new session:

```sh
claude --plugin-dir .
```

In Codex, install the plugin from this repository's marketplace and trust the MCP server.
Start a new session after installation.

## MCP Tools

The upstream server exposes these tools.

| Tool | Description |
| --- | --- |
| `search_text` | Search the web for text results. |
| `search_images` | Search for images. |
| `search_news` | Search for news. |
| `search_videos` | Search for videos. |
| `search_books` | Search for books. |
| `extract_content` | Extract content from a URL. |

`search_text` requires `query` and accepts optional region, safe search, time limit, result count, page, and backend settings.
`extract_content` requires `url` and accepts an optional format such as `text_markdown` or `text_plain`.

The upstream package owns the tool schemas and their behavior.
This repository does not modify, wrap, or reimplement them.

## Package contents

- `.claude-plugin/plugin.json` declares the Claude Code plugin.
- `.codex-plugin/plugin.json` declares the Codex plugin.
- `.mcp.json` and `mcp.json` register the same stdio server for each host.
- `.claude-plugin/marketplace.json` and `.agents/plugins/marketplace.json` publish the self-marketplace.

## Verification

```sh
pnpm install --frozen-lockfile
pnpm run check
```

The check script validates the manifests, the issue forms, the plugin version format, Markdown, and type-aware lint.
See [CONTRIBUTING.md](CONTRIBUTING.md) for the contribution procedure.
