# Matrix Series Kether Guidance

Use Kether only where the target plugin already supports it.

## Current supported uses

- `MatrixShop`
  - tax `Condition`
  - discount `condition`
  - refresh matching scripts
- `MatrixStorage`
  - unlock `Conditions`
  - future action hooks if explicitly requested
- `MatrixCook`
  - recipe success/failure actions

## Output rules

- Output real Kether lines, not prose.
- Keep each condition/action small and composable.
- Prefer permission, placeholder, numeric compare, and simple boolean flow.
- When generating multiple conditions, emit them as YAML string lists.

## Example conditions

```yaml
Conditions:
  - "perm 'matrixstorage.warehouse.unlock.45'"
  - "check papi \"%player_level%\" >= 20"
```

## Example action list

```yaml
Actions:
  - "tell \"&a解锁成功\""
  - "console \"lp user {player} permission set matrixstorage.warehouse.unlock.54\""
```

