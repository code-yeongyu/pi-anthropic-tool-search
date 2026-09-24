# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

## [0.1.1] - 2026-09-24

### Changed

- Migrate peer dependencies from `@mariozechner/pi-*` to `@earendil-works/pi-*` scope
- Upgrade all devDependencies to latest: @biomejs/biome 2.5.14, typescript 7.0.2, vitest 5.0.1, @types/node 26.6.2, @typescript/native-preview 7.0.0-dev.20260707.2
- Require Node.js >=22.19.0
- Add Bun 1.4.2 CI workflow (ubuntu-latest, macos-latest × node 22, 24)
- Generate bun.lock and package-lock.json

### Fixed

- Biome config preset deprecation

## [0.1.0] - 2026-05-07

### Added

- Initial pi coding-agent extension that mirrors senpi builtin `anthropic-tool-search` and injects Anthropic native tool-search tools based on `PI_ANTHROPIC_TOOL_SEARCH`.
