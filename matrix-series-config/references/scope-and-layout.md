# Matrix Series Scope And Layout

## Supported plugins

- `MatrixLib`
- `MatrixShop`
- `MatrixStorage`
- `MatrixAuth`
- `MatrixCook`

## Primary goals

Use this skill when the user wants:

- new starter configs
- config migration
- config cleanup
- config explanation
- Kether condition or action scripts
- a pack that spans multiple Matrix plugins

## Output discipline

- Use current plugin directory layout.
- Prefer current repo paths over historical handoff structure.
- Split output by file path.
- Keep business logic in the target plugin's supported config model.
- For currencies, use `MatrixLib` as the source of truth.

