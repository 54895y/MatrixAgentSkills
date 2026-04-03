# MatrixCook Config Surface

## Core layout

```text
plugins/MatrixCook/
├─ config.yml
├─ cooker/
├─ recipe/
├─ fuel/
├─ categories/
├─ ui/
└─ language/
```

## Main areas

- `config.yml`
  - language
  - hologram
  - cooking timeout
  - placed cooker storage backend
- `cooker/*.yml`
  - hand item
  - placed source/type/id
  - speed and recipe allow list
  - GUI layout
- `recipe/*.yml`
  - ingredients
  - cooking time
  - success item and actions
  - failure item and actions
- `fuel/*.yml`
  - item matcher
  - burn time
- `categories/*.yml`
  - menu grouping

## Kether

`result.actions` and `failure.actions` may contain Kether actions.

