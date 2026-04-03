# MatrixAuth Config Surface

## Core layout

```text
plugins/MatrixAuth/
├─ config.yml
├─ messages.yml
└─ settings/
   ├─ guide.yml
   └─ easybot.yml
```

## Main areas

- `config.yml`
  - default login mode
  - Mojang API
  - SQLite/MySQL storage
  - debug
  - placeholder display text
  - bedrock compatibility
- `messages.yml`
  - player-facing text
  - help pages
  - command feedback
- `settings/guide.yml`
  - guide and reminder flow
- `settings/easybot.yml`
  - HTTP query integration for EasyBot

## Output rule

MatrixAuth config work should stay within these real files. Do not invent shop-style directories.

