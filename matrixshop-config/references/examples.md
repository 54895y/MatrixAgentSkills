# MatrixShop Examples

## 1. Economy module

```yaml
vault:
  Mode: vault
  Display-Name: "金币"
  Symbol: "$"
  Decimal: true

playerpoints:
  Mode: playerpoints
  Display-Name: "点券"
  Symbol: "点"
  Decimal: false
```

## 2. SystemShop settings

```yaml
Enabled: true

Bindings:
  Commands:
    Bindings:
      - 'system'
      - 'systemshop'
    Register: false
    Show-In-Help: true
    Priority: 100
    Help-Key: '@commands.bindings.system-shop'
    Help:
      - '&7系统商店使用静态商品配置。'
      - '&7常用入口: &f{command} open <分类>'
    Condition: 'perm matrixshop.systemshop.use'

Currency:
  Key: vault
```

## 3. SystemShop category

```yaml
Title:
  - '&8武器商店'

layout:
  - '#########'
  - '#ggggggg#'
  - '#ggggggg#'
  - '####I####'
  - '####R####'

template:
  name: '&f{name}'
  lore:
    - '&7价格: &e{price} {currency}'
    - '&7单次上限: &f{limit}'

Currency:
  Key: vault

goods:
  - diamond_sword
```

## 4. SystemShop goods file

```yaml
id: diamond_sword
material: 'DIAMOND_SWORD'
amount: 1
price: 420
buy-max: 8
name: '&b钻石剑'
lore:
  - '&7高品质近战武器'
```

## 5. SystemShop goods group

```yaml
id: starter_weapons
Kind: group
entries:
  - wooden_sword
  - iron_sword
  - bow
```

## 6. SystemShop refresh pool

```yaml
id: weapon_refresh_pool_example
Kind: pool
entries:
  iron_sword_offer:
    goods: iron_sword
    weight: 10
    price: 99
    buy-max: 3
```

## 7. SystemShop category with refresh area

```yaml
Title:
  - '&8武器商店'

layout:
  - '#########'
  - '#ggggggg#'
  - '#ggggggg#'
  - '####I####'
  - '####R####'

icons:
  '#':
    material: 'STAINED_GLASS_PANE'
    name: ' '
  'g':
    material: 'AIR'
    mode: 'goods'
    refresh:
      Enabled: true
      Cron: '0 0 6 * * ?'
      Timezone: 'Asia/Shanghai'
      Same-For-Players-In-Group: true
      groups:
        default:
          Enabled: true
          Random-Refresh: true
          Pick: 2
          Pool-Ref: 'weapon_refresh_pool_example'
  'I':
    material: 'BOOK'
    name: '&f商店说明'
  'R':
    material: 'BARRIER'
    name: '&c返回'
    actions:
      left:
        - 'back'

template:
  name: '&f{name}'
  lore:
    - '&7价格: &e{price} {currency}'
    - '&7单次上限: &f{limit}'

Currency:
  Key: vault

goods:
  - starter_weapons
```

## 8. PlayerShop settings

```yaml
Enabled: true

Bindings:
  Commands:
    Bindings:
      - 'player_shop'
      - 'playershop'
      - 'pshop'
    Register: false
    Show-In-Help: true
    Priority: 90
    Condition: 'perm matrixshop.playershop.use'

Unlock:
  Base: 21
  Max: 100

Search:
  enable: true
  condition: "perm shop.vip"

Listing:
  Tax:
    Enabled: true
    Mode: percent
    Value: 3.0
    Rules:
      vip:
        Enabled: true
        Priority: 100
        Mode: percent
        Value: 1.0
        Condition:
          - "perm 'group.vip'"

Currency:
  Key: vault
```

## 9. GlobalMarket tax config

```yaml
Listing:
  Expire-Hours: 72
  Tax:
    Enabled: true
    Mode: percent
    Value: 3.0
    Rules:
      vip:
        Enabled: true
        Priority: 100
        Mode: percent
        Value: 1.0
        Condition:
          - "perm 'group.vip'"
```

## 10. Transaction tax config

```yaml
Options:
  Trade:
    Allow-Items: true
    Allow-Money: true
    Allow-Exp: true
    Tax:
      Enabled: true
      Mode: percent
      Value: 3.0
      Rules:
        vip:
          Enabled: true
          Priority: 100
          Mode: percent
          Value: 1.0
          Condition:
            - "perm 'group.vip'"
```

## 11. ChestShop tax config

```yaml
Trade:
  Tax:
    Enabled: true
    Mode: percent
    Value: 3.0
    Rules:
      vip:
        Enabled: true
        Priority: 100
        Mode: percent
        Value: 1.0
        Condition:
          - "perm 'group.vip'"
```

## 12. Non-shop module bindings

For modules such as `ChestShop`, `Cart`, and `Record`, put bindings in `settings.yml`:

```yaml
Bindings:
  Commands:
    Bindings:
      - 'cart'
    Register: true
    Show-In-Help: true
    Help:
      - '&7购物车用于统一结算多个商品来源。'
      - '&7常用入口: &f{command} open'
```

## 13. Help and hint keys

For shop-based modules:

```yaml
Bindings:
  Commands:
    Help-Key: '@commands.bindings.auction'
    Hint-Keys:
      open: '@commands.help.desc.auction-open'
      upload-english: '@commands.hints.auction-upload-english'
```
