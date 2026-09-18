# Repository Guidelines

## Project Structure & Module Organization

This repository is currently a minimal scaffold: no application source, tests, or build configuration are tracked yet. The root contains `.mcp.json`, which declares MCP server configuration and is presently empty.

When adding the first implementation, keep the layout conventional and easy to navigate:

- `src/` for application or library code.
- `tests/` for automated tests that mirror `src/` paths.
- `assets/` for static files such as images or fixtures.
- `docs/` for design notes or longer operational documentation.

Avoid adding empty directories or speculative abstractions. Group code by feature once multiple related files exist.

## Build, Test, and Development Commands

No build, test, lint, or run commands are configured yet. Do not assume commands such as `npm test` or `make build` work. When introducing tooling, expose a small, documented command set through the ecosystem's standard entry point (for example, `package.json`, `pyproject.toml`, or `Makefile`). Update this guide in the same change.

Before submitting changes, always run:

```sh
git status --short
git diff --check
```

These commands confirm the intended files changed and catch whitespace errors.

## Coding Style & Naming Conventions

Follow the formatter and linter native to the language selected by the project. Commit their configuration with the first source files. Until then, use UTF-8, Unix line endings, spaces rather than tabs, and a final newline.

Use descriptive names: `snake_case` for Python modules, `kebab-case` for documentation files, and the language's standard convention for types and functions. Keep configuration at the repository root and never commit credentials to `.mcp.json` or other files.

## Testing Guidelines

Add tests with every non-trivial behavior change. Mirror source paths under `tests/` and use the framework's discoverable naming convention, such as `test_*.py` or `*.test.ts`. Bug fixes should include a focused regression test. Document any required environment variables and test command here.

## Commit & Pull Request Guidelines

History currently contains only `Initial commit`, so no project-specific convention exists. Use short, imperative subjects such as `Add document parser` or `Fix empty input handling`.

Pull requests should explain the purpose, summarize verification performed, and link relevant issues. Include screenshots only for visible UI changes. Keep each pull request focused and call out configuration or compatibility changes explicitly.
