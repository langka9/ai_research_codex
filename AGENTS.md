# Repository Guidelines

## Project Structure & Module Organization

This checkout currently has no application code, tests, assets, build manifests, or Git metadata. As the project is established, keep implementation in `src/`, mirror its feature layout under `tests/`, place reusable examples or static files in `assets/`, and put design or usage notes in `docs/`. Keep each module focused on one research workflow or capability.

## Build, Test, and Development Commands

No build, run, or test commands are configured yet. When adding a language or framework, document its setup and the exact commands for local development, tests, and linting here (for example, the package-manager test command). Do not assume a command succeeds until its toolchain and configuration are checked in.

## Coding Style & Naming Conventions

No formatter or language-specific style configuration exists yet. Follow the conventions and formatter of the language selected for each component, and check in shared configuration so contributors get consistent results. Use descriptive, feature-oriented names; keep Markdown files UTF-8 with clear headings and concise examples.

## Testing Guidelines

There is no test framework or coverage requirement in this checkout. Add tests under `tests/`, using names that identify the feature or behavior they cover, and document a single reproducible test command when a test runner is introduced. Include a regression test when fixing a defect.

## Commit & Pull Request Guidelines

No Git history is available to establish an existing commit convention. Use short, imperative commit subjects such as `Add paper search workflow`. Pull requests should explain the change and its motivation, list validation performed, link related issues when applicable, and include screenshots for UI or visual changes.

## Security & Configuration

Keep credentials and machine-specific settings out of source control. Use environment variables or ignored local configuration for secrets, and provide sanitized example configuration when setup requires it.
