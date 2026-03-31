# MatrixShop Migration Guidance

Use this reference when the user wants to migrate from another shop plugin into MatrixShop.

## Scope

Common migration targets:

- `UltimateShop`
- `EconomyShopGUI`
- `Shopkeepers`
- `QuickShop`

## Mapping Principles

### Static GUI shops

Source plugins that define static categories and priced items should usually map to:

- `SystemShop/settings.yml`
- `SystemShop/shops/*.yml`
- `SystemShop/ui/*.yml`

Typical sources:

- `UltimateShop`
- `EconomyShopGUI`

### Player-driven markets

Source plugins that focus on player-owned listings or open markets should usually map to:

- `PlayerShop`
- `GlobalMarket`
- `Auction`

### Chest-based shops

Source plugins that use physical chests or signs should usually map to:

- `ChestShop`

Typical sources:

- `QuickShop`

## Migration Output Rules

- Do not preserve the original plugin's key names if MatrixShop already has a stable equivalent.
- Prefer MatrixShop-native filenames and directories.
- If the source plugin mixes economy and display config together, split them into MatrixShop's module, shop, and economy layers.
- If the source plugin has unsupported behavior, state the difference briefly and generate the closest supported MatrixShop structure.

## Common Mappings

### UltimateShop -> SystemShop

- source category -> `SystemShop/shops/<category>.yml`
- source item definition -> `SystemShop/goods/<id>.yml`
- source category listing -> `SystemShop/shops/<category>.yml` -> `goods:`
- source item price -> `SystemShop/goods/<id>.yml` -> `price`
- source item limit -> `SystemShop/goods/<id>.yml` -> `buy-max`
- source item display -> `name`, `lore`, `material`, optional `item`
- source currency -> product-level `currency` in the goods file, or shop-level `Currency.Key`

### EconomyShopGUI -> SystemShop

- source section/shop page -> `SystemShop/shops/<page>.yml`
- shop title -> `Title`
- icon layout -> `layout` + `icons`
- product entries -> `SystemShop/goods/*.yml` + `SystemShop/shops/<page>.yml` -> `goods:`
- worth/price -> `price`

### QuickShop -> ChestShop

- do not try to convert QuickShop into `SystemShop`
- map it into `ChestShop` module behavior and settings instead

## Recommended User Prompts

- `把这份 UltimateShop 配置迁移成 MatrixShop 的 SystemShop`
- `把这份 EconomyShopGUI 商店页迁移成 MatrixShop/shops/*.yml`
- `把这份 QuickShop 需求转成 MatrixShop ChestShop 设置`
