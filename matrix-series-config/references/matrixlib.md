# MatrixLib Config Surface

## Shared economy

Primary file:

```text
plugins/MatrixLib/Economy/currency.yml
```

Runtime sync targets:

- `plugins/MatrixShop/Economy/currency.yml`
- `plugins/MatrixStorage/Economy/currency.yml`

## Currency model

Each top-level key is one currency channel:

```yaml
vault:
  Mode: vault
  Display-Name: "金币"
  Symbol: "$"
  Decimal: true
```

Supported `Mode` values:

- `vault`
- `playerpoints`
- PlaceholderAPI placeholder string such as `%custom_points%`

Supported action blocks:

- `Actions.Take`
- `Actions.Give`
- `Actions.Deny`

Prefer `console:`, `player:`, and `tell:` actions.

