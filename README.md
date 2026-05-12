# pi-anthropic-tool-search

[![ci](https://github.com/code-yeongyu/pi-anthropic-tool-search/actions/workflows/ci.yml/badge.svg)](https://github.com/code-yeongyu/pi-anthropic-tool-search/actions/workflows/ci.yml) [![license: MIT](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)

Anthropic native tool-search extension for the [pi coding agent](https://github.com/badlogic/pi-mono/tree/main/packages/coding-agent).

This package is the standalone extraction of senpi's former builtin `anthropic-tool-search` extension.

## Behavior

The extension does not register new local tools. It intercepts Anthropic requests and conditionally adds native Anthropic tool-search tools based on `PI_ANTHROPIC_TOOL_SEARCH`.

Supported modes:

- `off` (default): no changes
- `regex`: inject `tool_search_tool_regex`
- `bm25`: inject `tool_search_tool_bm25`
- `both`: inject both tools

Function-style variants with the same names are stripped when native types are not used. Invalid env values are treated as `off`; the extension emits one warning notification per session for invalid values.

It also appends a system-prompt section for Anthropic sessions when tool search mode is enabled.

## Installation

The package targets the [`pi`](https://github.com/badlogic/pi-mono/tree/main/packages/coding-agent) coding agent. Pi loads extensions from `~/.pi/agent/extensions/`, project `.pi/extensions/`, or via the `--extension` / `-e` CLI flag.

```bash
# From npm (once published)
pi install npm:pi-anthropic-tool-search

# From git
pi install git:github.com/code-yeongyu/pi-anthropic-tool-search

# Manual placement
git clone https://github.com/code-yeongyu/pi-anthropic-tool-search ~/.pi/agent/extensions/pi-anthropic-tool-search
cd ~/.pi/agent/extensions/pi-anthropic-tool-search && npm install

# Dev / one-shot test
pi -e /path/to/pi-anthropic-tool-search/src/index.ts
```

After installation, restart pi or run `/reload` inside an interactive session.

## Development

```bash
npm install
npm test
npm run typecheck
npm run check
pi -e ./src/index.ts
```

The test suite uses vitest. TypeScript is strict, Node-only, and uses ESM imports with `.js` suffixes.

## Origin

Ported from `packages/coding-agent/src/core/extensions/builtin/anthropic-tool-search/index.ts` in `code-yeongyu/senpi-mono`.

## License

[MIT](LICENSE).
