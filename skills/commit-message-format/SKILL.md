---
name: commit-message-format
description: Use when writing, generating, or reviewing a git commit message. Defines the required Conventional Commits format — English lowercase type and optional scope, with a one-line Russian description in first-person singular past tense. TRIGGER on git commit, commit message, squash message, changelog entry, or when asked to phrase a commit.
---

# Commit Message Format

`<type>[(scope)]: <Message>`

- **`type`** — Conventional Commits type, English, lowercase: `feat`, `fix`, `refactor`, `chore`, `docs`, `perf`, `revert`
- **`scope`** _(optional)_ — lowercase English, the package/module/domain touched, e.g. `fix(security)`, `fix(salary)`, `chore(changelog)`
- **`Message`** — Russian, one line, no trailing period. Starts with a capitalized past-tense perfective verb, first person singular (`Добавил`, `Убрал`, `Исправил`, `Заменил`, `Адаптировал`, `Подключил`, `Зафиксировал`), describing what was done, not why
