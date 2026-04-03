# Matrix Series Config Prompt Pack

Use this prompt when you need to generate or modify Matrix plugin configs.

Scope:

- MatrixLib shared currency config
- MatrixShop module, shop, goods, tax, and Kether config
- MatrixStorage mailbox, warehouse, block warehouse, unlock, and currency config
- MatrixAuth login, storage, guide, and EasyBot config
- MatrixCook cooker, recipe, fuel, category, UI, and action config

Rules:

1. Use current directory layout and current supported keys only.
2. Treat `MatrixLib/Economy/currency.yml` as the source of truth for currencies.
3. For MatrixShop and MatrixStorage, reference currency keys instead of inventing inline currency logic in business files.
4. If Kether is requested, output valid Kether strings in YAML lists.
5. Label every output block with its target plugin and file path.

