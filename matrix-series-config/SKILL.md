---
name: matrix-series-config
description: Use when users want to generate, modify, migrate, or explain YAML configuration for MatrixLib, MatrixShop, MatrixStorage, MatrixAuth, or MatrixCook, including shared currency definitions, mailbox and warehouse unlock rules, storage backends, shop YAML files, login settings, cooker and recipe files, and Kether conditions or action scripts used by the Matrix plugin series.
---

# Matrix Series Config

Use this skill for Matrix series configuration work. Do not use it for Kotlin source edits unless the user is explicitly changing plugin code.

## Workflow

1. Read `references/scope-and-layout.md`.
2. Read the plugin-specific reference file that matches the user's target plugin.
3. If the request includes Kether conditions or actions, read `references/kether.md`.
4. If the user needs ready-to-paste YAML, read `references/examples.md`.
5. Generate only current supported keys and current directory layout.

## Current Rules

- `MatrixLib` is the shared entrypoint for `Economy/currency.yml`.
- Runtime currency files are synchronized across:
  - `plugins/MatrixLib/Economy/currency.yml`
  - `plugins/MatrixShop/Economy/currency.yml`
  - `plugins/MatrixStorage/Economy/currency.yml`
- `MatrixShop` business configs should reference currency keys, not inline currency actions inside shop files.
- `MatrixStorage` supports mailbox and warehouse slot unlocks with:
  - multiple conditions
  - multiple prices
  - multiple currencies in one unlock rule
- `MatrixAuth` uses:
  - `config.yml`
  - `messages.yml`
  - `settings/guide.yml`
  - `settings/easybot.yml`
- `MatrixCook` uses:
  - `config.yml`
  - `cooker/*.yml`
  - `recipe/*.yml`
  - `fuel/*.yml`
  - `categories/*.yml`
  - `ui/*.yml`
- Kether is valid for Matrix series config output when the target plugin already supports conditions or scripted actions.

## Output Rules

- Prefer full file output with a clear path label.
- Produce valid YAML or valid Kether, not pseudo-syntax.
- Preserve the user's language.
- Do not invent unsupported files or keys.
- When multiple Matrix plugins are involved, separate output by plugin and target path.

## References

- `references/scope-and-layout.md`
  - Always read first.
- `references/matrixlib.md`
  - Read for shared currency definitions and synchronization behavior.
- `references/matrixshop.md`
  - Read for shop, goods, tax, and currency-key rules.
- `references/matrixstorage.md`
  - Read for mailbox, warehouse, block warehouse, and unlock config.
- `references/matrixauth.md`
  - Read for login, storage, guide, and EasyBot config.
- `references/matrixcook.md`
  - Read for cooker, recipe, fuel, category, and storage config.
- `references/kether.md`
  - Read when conditions or scripted actions are requested.
- `references/examples.md`
  - Read when the user wants generated starter configs or merged config packs.

