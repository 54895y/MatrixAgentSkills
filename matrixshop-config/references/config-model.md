# MatrixShop Config Model

## Core directory layout

```text
plugins/MatrixShop/
├─ config.yml
├─ module.yml
├─ database.yml
├─ Economy/
├─ Menu/
├─ SystemShop/
│  ├─ goods/
│  ├─ shops/
│  └─ ui/
├─ PlayerShop/
├─ GlobalMarket/
├─ Auction/
├─ ChestShop/
├─ Transaction/
├─ Cart/
└─ Record/
```

## Module split

### Shop-based modules

These use `shops/*.yml` as real entry files:

- `Menu`
- `SystemShop`
- `PlayerShop`
- `GlobalMarket`
- `Auction`
- `Transaction`

Rules:

- `shopId` is the filename, not a YAML `id` field.
- `Bindings.Commands`
- `Help`
- `Help-Key`
- `Hint-Keys`
- `Condition`

belong in the shop file.

### Non-shop modules

These do not use `shops/*.yml`:

- `ChestShop`
- `Cart`
- `Record`

Rules:

- bindings live in `settings.yml`
- help blocks also live in `settings.yml`
- they use module-level UI files only

## Economy rules

### Mandatory module

`Economy` is a core module. It is always enabled.

### Currency priority

1. product-level
2. shop-level
3. module-level
4. fallback `vault`

### Scope by module

- `SystemShop`
  - product-level: yes
  - shop-level: yes
  - module-level: yes
- `PlayerShop`
  - product-level: no
  - shop-level: yes
  - module-level: yes
- `GlobalMarket`
  - product-level: no
  - shop-level: yes
  - module-level: yes
- `Auction`
  - product-level: no
  - shop-level: yes
  - module-level: yes
- `Transaction`
  - product-level: no
  - shop-level: yes
  - module-level: yes
- `ChestShop`
  - product-level: no
  - shop-level: no
  - module-level: yes
- `Cart`
  - no business currency config
- `Record`
  - no business currency config

## Bindings rules

### Commands

`Bindings.Commands` can include:

- `Bindings`
- `Register`
- `Show-In-Help`
- `Priority`
- `Condition`
- `Help`
- `Help-Key`
- `Hint-Keys`

### Condition

`Condition` is a Kether action string.

### Help

`Help` is a multiline help block.

`Help-Key` and `Hint-Keys` are language-key style indirections for help and subcommand hint text.

### Placeholders

The current help and hint chain supports:

- `{command}`
- `{binding}`
- `{shop-id}`
- `{shop}`

## SystemShop goods

`SystemShop/goods/*.yml` can currently be used in three ways:

- product file
- `Kind: group`
- `Kind: pool`

### Product fields

`SystemShop` product files currently support:

- `material`
- `item`
- `amount`
- `price`
- `buy-max`
- `name`
- `lore`
- `currency`

If `item` is present, it should be treated as the higher-fidelity product source for item metadata.

Preferred storage model:

- `SystemShop/goods/<product-id>.yml`
  - stores one reusable product definition
- `SystemShop/shops/<shop-id>.yml`
  - uses `goods:` as a list of product ids, for example:

```yaml
goods:
  - diamond_sword
  - bow
```

Legacy-compatible model:

- `SystemShop/shops/<shop-id>.yml`
  - may still embed `goods.<id>` sections directly

When generating fresh configs, prefer the separate `goods/` directory plus shop references.

### Group resource

Use `Kind: group` when multiple products should be reused together:

```yaml
id: starter_weapons
Kind: group
entries:
  - wooden_sword
  - iron_sword
  - bow
```

### Pool resource

Use `Kind: pool` for refreshable weighted candidates:

```yaml
id: weapon_refresh_pool_example
Kind: pool
entries:
  iron_sword_offer:
    goods: iron_sword
    weight: 10
    price: 99
    buy-max: 3
```

## SystemShop refresh

Refresh config belongs in the category shop file under `icons.<char>.refresh`.

Supported structure:

- `Enabled`
- `Cron`
- `Timezone`
- `Same-For-Players-In-Group`
- `groups.<id>.Enabled`
- `groups.<id>.Match-Script`
- `groups.<id>.Random-Refresh`
- `groups.<id>.Pick`
- `groups.<id>.Pool-Ref`
- `groups.<id>.goods`

Meaning:

- `Pool-Ref` points to a `Kind: pool` goods resource
- `goods` can directly reference products or `Kind: group` resources
- `Match-Script` is used to route players into different refresh groups

## SystemShop admin UI files

Current default resources include:

- `SystemShop/ui/goods-browser.yml`
- `SystemShop/ui/goods-editor.yml`
- `SystemShop/ui/goods-shops.yml`

These are real UI resources, but the related admin commands are not configuration keys and should not be emitted as YAML fields.
