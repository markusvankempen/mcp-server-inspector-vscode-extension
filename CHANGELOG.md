# Changelog

**Author:** Markus van Kempen  
[Research | Floor 7½ 🏢🤏](https://markusvankempen.github.io/)

## 1.6.0
- **Protocol client:** list calls follow `nextCursor` until every page is fetched, `MCP-Protocol-Version` is sent after `initialize`, and Server-Sent Events are parsed event by event. The client answers `ping` and `roots/list`, and replies "method not found" to any other server request so the server is not left waiting.
- **Spec audit:** checks `ping` and renders the first prompt with `prompts/get`. Roots, sampling and elicitation are client capabilities: they count as supported only when the server is seen using them, and are otherwise shown as not scored.
- **Raw console:** `ping` and `prompts/get` templates. The popup audit tab renders the report.
- New Chrome Web Store zip and VS Code package.

## 1.5.0
- **Security Hygiene (Tier 5):** new Workbench section with its own score. Scans tool metadata for hidden Unicode characters, injection-style wording, credential-file references, encoded blobs, oversized descriptions, duplicate or malformed names and destructive tools without safety hints.
- **Tool fingerprint (rug-pull detection):** SHA-256 per tool definition, stored per endpoint; changes after you accepted a baseline are reported and can be accepted with one click.
- **Opt-in active probes** (off by default): unauthenticated access, Origin validation (VS Code edition), OAuth protected-resource discovery, HSTS, CORS, server banner, error-message leakage and session-ID quality.
- Shared report renderer for the Crypto Posture and Security Hygiene sections; new `test:security` suite.

## 1.4.0
- **Crypto Posture (Tier 4):** new Workbench section with a separate score for scheme, TLS version, cipher suite, key-exchange group (hybrid post-quantum vs classical), certificate and JWT header algorithm, plus a CycloneDX CBOM fragment export. TLS probing runs in the extension host with `node:tls`; certificate validation is never disabled.
- New preset: hosted reference server `https://mcp-reference-server-102.vercel.app/mcp`.

## 1.3.1
- **SEP-19 / SEP-21 Progressive Disclosure Groups (v1.0.2 Update):** Added support for root-level scoped `tools`, `prompts`, `resources`, and nested `groups` in `groups/get` responses while maintaining backward compatibility with `contents.tools`.
- **Marketplace Publishing Package:** Updated extension identifier to `mcp-server-inspector-auditor` with bundled icon and optimized packaging.
- **Enhanced Test Suite & Port Handling:** Robust ephemeral fallback port allocation during automated testing to avoid port collisions.

## 1.3.0
- **Local dev server:** the sample mock MCP server is bundled with the extension. Start/stop it from the Server view, the Explorer welcome link or the Command Palette (*Start/Stop Local Dev Server*); it binds to `127.0.0.1` only and the session connects to it automatically.
- New setting `mcpInspector.devServer.port` (default 3000, range 1024-65535); a busy port is reported with a clear message.
- The server is stopped automatically when the extension deactivates.

## 1.2.2
- Initial VS Code release, sharing the workbench UI and protocol libraries with the Chrome extension.
- Activity Bar container with three views: **Server** (connect + stats), **Explorer** (native tree of tools, resources, prompts, groups) and **Workbench** (the workbench navigation as a native tree).
- Run tools with parameters: arguments editor generated from the tool's schema, Run CodeLens, results in a read-only JSON editor beside it. Resources open in the same result editor.
- One shared MCP connection in the extension host; the workbench hides its own left navigation and opens at the selected section.
- Toolbar icon in the editor title bar and a status bar button to launch the workbench.
- Network requests run in the extension host; credentials are kept in SecretStorage.
