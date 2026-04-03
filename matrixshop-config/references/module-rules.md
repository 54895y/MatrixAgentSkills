# MatrixShop Module Rules

## Economy

Files:

- `Economy/currency.yml`

Use it to define:

- `vault`
- `playerpoints`
- placeholder-driven custom currencies

## Menu

Files:

- `Menu/settings.yml`
- `Menu/shops/*.yml`
- `Menu/ui/*.yml`

Notes:

- shop-based module
- usually acts as a hub to open other modules

## SystemShop

Files:

- `SystemShop/settings.yml`
- `SystemShop/goods/*.yml`
- `SystemShop/shops/*.yml`
- `SystemShop/ui/*.yml`

Notes:

- static goods configuration
- prefer storing products in `SystemShop/goods/*.yml`
- `SystemShop/goods/*.yml` can also define `Kind: group` and `Kind: pool` resources
- `SystemShop/shops/*.yml` should usually reference products with `goods:`
- inline goods in the shop file are legacy-compatible only
- product-level currency is supported
- refresh rules belong in `SystemShop/shops/*.yml` under `icons.<char>.refresh`
- default admin UI resources include `SystemShop/ui/goods-browser.yml`, `goods-editor.yml`, and `goods-shops.yml`
- admin commands such as `goods save`, `goods add`, and `refresh run` are operational commands, not YAML keys

## PlayerShop

Files:

- `PlayerShop/settings.yml`
- `PlayerShop/shops/*.yml`
- `PlayerShop/ui/*.yml`

Notes:

- player-owned listings
- shop file controls browse entry and shop-level settings
- conditional tax config belongs in `PlayerShop/settings.yml -> Listing.Tax`

## GlobalMarket

Files:

- `GlobalMarket/settings.yml`
- `GlobalMarket/shops/*.yml`
- `GlobalMarket/ui/*.yml`

Notes:

- shop file controls one market entry
- shop-level currency is supported
- conditional tax config belongs in `GlobalMarket/settings.yml -> Listing.Tax`
- legacy `Listing.Tax-Percent` may still appear in old configs

## Auction

Files:

- `Auction/settings.yml`
- `Auction/shops/*.yml`
- `Auction/ui/*.yml`

Notes:

- supports `ENGLISH` and `DUTCH`
- shop-level currency is supported
- conditional tax config belongs in `Auction/settings.yml -> Options.Listing.Tax`

## Transaction

Files:

- `Transaction/settings.yml`
- `Transaction/shops/*.yml`
- `Transaction/ui/*.yml`

Notes:

- request / trade / confirm flow
- shop-level currency is supported
- money tax config belongs in `Transaction/settings.yml -> Options.Trade.Tax`

## ChestShop

Files:

- `ChestShop/settings.yml`
- `ChestShop/signs.yml`
- `ChestShop/ui/*.yml`

Notes:

- no `shops/*.yml`
- bindings live in `settings.yml`
- module-level currency only
- conditional tax config belongs in `ChestShop/settings.yml -> Trade.Tax`

## Cart

Files:

- `Cart/settings.yml`
- `Cart/ui/*.yml`

Notes:

- no `shops/*.yml`
- no business currency definition

## Record

Files:

- `Record/settings.yml`
- `Record/retention.yml`
- `Record/ui/*.yml`

Notes:

- no `shops/*.yml`
- no business currency definition
