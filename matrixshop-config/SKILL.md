---
name: matrixshop-config
description: Use when users want to generate, modify, migrate, or explain MatrixShop configuration files, including module switches, bindings, help text, economy definitions, SystemShop goods, and module or shop YAML files, based on the current MatrixShop configuration model.
---

# MatrixShop Config

Use this skill for MatrixShop YAML configuration work. Do not use it for Kotlin code changes unless the user is explicitly editing plugin source.

## Workflow

1. Read `references/config-model.md`.
2. If the task targets specific modules, read `references/module-rules.md`.
3. If the user needs concrete YAML, read `references/examples.md`.
4. Decide the exact target file path before generating content.
5. Generate only supported keys and current MatrixShop structures.

## Current Rules

- Shop-based modules:
  - `Menu`
  - `SystemShop`
  - `PlayerShop`
  - `GlobalMarket`
  - `Auction`
  - `Transaction`
- Non-shop modules:
  - `ChestShop`
  - `Cart`
  - `Record`
- `Economy` is mandatory and should not be disabled.
- For shop-based modules, the shop id is the `shops/<filename>.yml` filename.
- For shop-based modules, `Bindings.Commands`, `Help`, `Help-Key`, and `Hint-Keys` belong in the shop file.
- For non-shop modules, bindings and help configuration belong in `settings.yml`.
- Currency priority is:
  1. product-level
  2. shop-level
  3. module-level
  4. fallback `vault`
- `ChestShop` uses module-level currency only.
- `Cart` and `Record` do not define business currency.
- `SystemShop` goods support product-level `currency`.
- Prefer `SystemShop/goods/*.yml` as reusable product files, then reference those ids from `SystemShop/shops/*.yml` under `goods:`.
- Inline `goods.<id>` blocks inside `SystemShop/shops/*.yml` are legacy-compatible, but should not be the default output for new configs.
- Admin maintenance commands exist (`goods ui`, `goods save`, `goods add`, `goods select`, `goods edit`), but those commands are not config keys.

## Output Rules

- Prefer full file output with a clear path label.
- Produce valid YAML, not pseudo-YAML.
- Preserve the user's language.
- Do not invent unsupported fields.
- If converting configs from other shop plugins, rewrite them to current MatrixShop conventions instead of preserving the source plugin structure.

## When To Read References

- `references/config-model.md`
  - Always read first.
- `references/module-rules.md`
  - Read when the task targets one or more modules.
- `references/examples.md`
  - Read when the user wants generated config examples, starter files, or merged config packs.
