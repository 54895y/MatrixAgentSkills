# MatrixShop Config Surface

## Core layout

```text
plugins/MatrixShop/
├─ config.yml
├─ module.yml
├─ database.yml
├─ Economy/currency.yml
├─ Menu/
├─ SystemShop/
├─ PlayerShop/
├─ GlobalMarket/
├─ Auction/
├─ ChestShop/
├─ Transaction/
├─ Cart/
└─ Record/
```

## Currency rules

- Currency definitions come from `MatrixLib`.
- MatrixShop files should only reference currency keys.
- Priority:
  1. product-level `currency`
  2. shop-level `Currency.Key`
  3. module-level `Currency.Key`
  4. fallback `vault`

## Kether

Supported in:

- tax `Condition`
- discount `condition`
- refresh matching scripts

Do not invent inline currency action blocks inside shop files.

