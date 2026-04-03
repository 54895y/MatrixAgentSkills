# MatrixAgentSkills

Public skills and prompt packs for the Matrix plugin series.

Current package:

- `matrixshop-config`
- `matrix-series-config`

This repository is designed to support two use cases:

1. Native skill installation for Codex-style agents.
2. Direct GitHub-link import for common agents that work better with a portable Markdown rule or a knowledge base file.

## Quick Links

- Repo: `https://github.com/54895y/MatrixAgentSkills`
- Codex skill path: `https://github.com/54895y/MatrixAgentSkills/tree/main/matrixshop-config`
- Codex skill path: `https://github.com/54895y/MatrixAgentSkills/tree/main/matrix-series-config`
- Portable prompt: `https://raw.githubusercontent.com/54895y/MatrixAgentSkills/main/portable/matrixshop-config.md`
- Portable prompt: `https://raw.githubusercontent.com/54895y/MatrixAgentSkills/main/portable/matrix-series-config.md`
- AIChat knowledge base: `https://raw.githubusercontent.com/54895y/MatrixAgentSkills/main/aichat/matrixshop-config-kb.md`
- AIChat knowledge base: `https://raw.githubusercontent.com/54895y/MatrixAgentSkills/main/aichat/matrix-series-config-kb.md`

## Install By Agent

### Codex / OpenAI Skills

Use the native skill folder:

`https://github.com/54895y/MatrixAgentSkills/tree/main/matrixshop-config`

For Matrix 系列统一配置与 Kether 生成，优先使用：

`https://github.com/54895y/MatrixAgentSkills/tree/main/matrix-series-config`

If the agent supports Codex-style GitHub skill install, send that folder link directly.

### Claude Code / Gemini CLI / Cline / Roo / Continue

Use the portable prompt file:

`https://raw.githubusercontent.com/54895y/MatrixAgentSkills/main/portable/matrixshop-config.md`

For跨 Matrix 系列配置与 Kether 脚本，优先使用：

`https://raw.githubusercontent.com/54895y/MatrixAgentSkills/main/portable/matrix-series-config.md`

If the agent supports remote rules, commands, or prompt import, send the raw link directly. If it does not, copy the file into the agent's project rule or custom prompt location.

Dedicated entry files are also included:

- `claude/matrixshop-config.md`
- `claude/matrix-series-config.md`
- `gemini/matrixshop-config.md`
- `gemini/matrix-series-config.md`
- `cline/matrixshop-config.md`
- `cline/matrix-series-config.md`
- `roo/matrixshop-config.md`
- `roo/matrix-series-config.md`
- `continue/matrixshop-config.md`
- `continue/matrix-series-config.md`

### AIChat

Do not treat the Codex skill as the primary AIChat format.

For AIChat, import the knowledge file into the knowledge base:

`https://raw.githubusercontent.com/54895y/MatrixAgentSkills/main/aichat/matrixshop-config-kb.md`

或统一配置知识库：

`https://raw.githubusercontent.com/54895y/MatrixAgentSkills/main/aichat/matrix-series-config-kb.md`

Then ask for MatrixShop configuration directly, for example:

- `根据我的生存服需求生成 MatrixShop 的 module.yml、Economy/currency.yml 和一个 SystemShop 分类`
- `帮我生成一个拍卖模块配置，要求使用点券作为默认货币`
- `基于我的需求生成 PlayerShop、GlobalMarket 和 ChestShop 的默认配置`
- `帮我生成 MatrixLib、MatrixShop、MatrixStorage 三端同步的货币配置`
- `帮我写 MatrixStorage 的仓库扩容解锁规则和对应 Kether 条件`

## Repository Layout

```text
MatrixAgentSkills/
├─ matrixshop-config/       # Native Codex-style skill
├─ matrix-series-config/    # Multi-plugin Matrix config skill
├─ portable/                # Cross-agent prompt packs
├─ claude/                  # Claude-friendly entry file
├─ gemini/                  # Gemini-friendly entry file
├─ cline/                   # Cline-friendly entry file
├─ roo/                     # Roo-friendly entry file
├─ continue/                # Continue-friendly entry file
└─ aichat/                  # AIChat knowledge-base material
```

## Scope

This repository is for Matrix series plugin skills.

Future packages can be added here for:

- `matrixauth-*`
- `matrixcook-*`
- `matrixlib-*`
