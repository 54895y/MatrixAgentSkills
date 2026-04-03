# MatrixStorage Config Surface

## Core layout

```text
plugins/MatrixStorage/
├─ config.yml
├─ database.yml
├─ module.yml
├─ messages.yml
├─ Economy/currency.yml
├─ Mailbox/settings.yml
├─ Warehouse/settings.yml
└─ BlockWarehouse/settings.yml
```

## Mailbox

`Mailbox/settings.yml` can define:

- default display lore
- unlock base slots
- unlock rules

Unlock rules support:

- `Slots`
- `Conditions`
- `Prices`

`Prices` may contain multiple currencies.

## Warehouse

`Warehouse/settings.yml` can define:

- overview options
- unlock base slots
- unlock rules

## BlockWarehouse

`BlockWarehouse/settings.yml` defines placement entries:

- `source`
- `type`
- `id`
- `mode`
- `display-name`
- `inventory-size`

Supported `source`:

- `minecraft`
- `craftengine`
- `itemsadder`
- `nexo`

Supported `type`:

- `block`
- `furniture`

Supported `mode`:

- `terminal`
- `location`

