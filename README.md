# DDGS MCP

Search the web and extract page content through the upstream [DDGS](https://github.com/deedy5/ddgs) MCP server.

## Runtime

Install uv 0.11.0 or later with `uvx` on PATH and a Python version supported by DDGS. The plugin runs `uvx --from "ddgs[mcp]" --with pip-system-certs ddgs mcp`. It uses the operating system certificate store for package downloads and HTTPS requests.
Try `search_text` for a web search or `extract_content` to read a URL.

## Install

### Claude Code

```sh
claude plugin marketplace add ririnto/ddgs-plugin
claude plugin install ddgs-plugin@ddgs-plugin
```

### Codex

```sh
codex plugin marketplace add ririnto/ddgs-plugin
codex plugin add ddgs-plugin@ddgs-plugin
```

If you already use the Sinon marketplace in either client, install `ddgs-plugin@sinon`.

### Cursor

In **Customize**, choose **From GitHub Repository**, enter `https://github.com/ririnto/ddgs-plugin`, and install **DDGS MCP**.
Start a new Agent conversation after installation.

Report vulnerabilities through [private vulnerability reporting](https://github.com/ririnto/ddgs-plugin/security/advisories/new).
