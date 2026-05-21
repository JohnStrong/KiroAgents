# Kiro Agent Hooks

A collection of reusable [Kiro](https://kiro.dev) agent hooks designed to accelerate the develop-test-release cycle. These hooks automate repetitive tasks like test generation, documentation syncing, and coverage reporting — so you can focus on shipping code.

Fork it, use it, extend it.

## Getting Started

Copy the hook files from the relevant language folder into your project's `.kiro/hooks/` directory (or wherever your Kiro workspace expects them). Each hook is self-contained and can be used independently.

## Repository Structure

### JavaScript

Located in [`js/`](./js/) — hooks targeting JavaScript and Node.js projects.

| Hook | Purpose |
|------|---------|
| `generate-spec-tests` | Auto-generates spec test files for JS/MJS source files, mirroring folder structure |
| `delete-spec-tests` | Cleans up corresponding test files when a source file is deleted |
| `sync-documentation` | Keeps README docs in sync with code changes on save |
| `test-coverage-report` | Produces a timestamped markdown coverage gap report after task completion |

See the [js/README.md](./js/README.md) for detailed descriptions, triggers, and pre-conditions.

## Contributing

PRs and forks welcome. If you build hooks for other languages or runtimes, open a folder and follow the same pattern.

## License

Licensed under the Apache License 2.0 — see [LICENSE](./LICENSE) for details.
