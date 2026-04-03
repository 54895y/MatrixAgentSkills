# Matrix Series Examples

## Shared currency file

```yaml
vault:
  Mode: vault
  Display-Name: "金币"
  Symbol: "$"
  Decimal: true

playerpoints:
  Mode: playerpoints
  Display-Name: "点券"
  Decimal: false
```

## MatrixStorage warehouse unlock

```yaml
unlock:
  base-slots: 27
  rules:
    warehouse_45:
      Slots: 45
      Conditions:
        - "perm 'matrixstorage.warehouse.unlock.45'"
      Prices:
        - Currency: vault
          Amount: 2500
        - Currency: playerpoints
          Amount: 25
```

## MatrixStorage mailbox unlock

```yaml
unlock:
  base-slots: 9
  rules:
    inbox_27:
      Slots: 27
      Conditions:
        - "perm 'matrixstorage.mailbox.unlock.27'"
      Prices:
        - Currency: vault
          Amount: 1200
```

## MatrixShop shop-level currency reference

```yaml
Currency:
  Key: playerpoints
```

## MatrixCook result actions

```yaml
result:
  item:
    type: "COOKED_BEEF"
  actions:
    - "tell \"&a烹饪成功\""
```

