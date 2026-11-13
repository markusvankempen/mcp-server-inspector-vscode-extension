# Changelog

**Author:** Markus van Kempen  
[Research | Floor 7½ 🏢🤏](https://markusvankempen.github.io/)

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
