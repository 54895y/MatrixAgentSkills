# MatrixShop 配置知识库

本知识库用于让 AIChat 直接根据需求生成 MatrixShop 配置。

## 使用方式

把这个文件加入 AIChat 的知识库，然后直接提需求。

推荐提问方式：

- `根据我的生存服需求，生成 MatrixShop 的 module.yml、Economy/currency.yml 和一个 SystemShop 武器分类`
- `帮我生成一个使用点券的 Auction 配置`
- `我要一个不使用 shops 目录的 ChestShop、Cart、Record 配置`
- `把下面这份 UltimateShop 配置迁移成 MatrixShop 当前格式`
- `把下面这份 EconomyShopGUI 配置迁移成 MatrixShop 当前格式`

## 当前 MatrixShop 结构

```text
plugins/MatrixShop/
├─ config.yml
├─ module.yml
├─ database.yml
├─ Economy/
├─ Menu/
├─ SystemShop/
│  ├─ goods/
│  ├─ shops/
│  └─ ui/
├─ PlayerShop/
├─ GlobalMarket/
├─ Auction/
├─ ChestShop/
├─ Transaction/
├─ Cart/
└─ Record/
```

## 模块规则

### 使用 shops 目录的模块

- Menu
- SystemShop
- PlayerShop
- GlobalMarket
- Auction
- Transaction

规则：

- `shopId` 就是 `shops/<文件名>.yml` 的文件名
- `Bindings.Commands`
- `Help`
- `Help-Key`
- `Hint-Keys`
- `Condition`

这些键应写在 shop 文件中

### 不使用 shops 目录的模块

- ChestShop
- Cart
- Record

规则：

- 这些模块只使用 `settings.yml` 和 `ui/*.yml`
- 绑定命令、帮助提示也写在 `settings.yml`

## Economy 规则

### Economy 模块

`Economy` 是核心模块，必须开启。

### 货币优先级

1. 商品级
2. 商店级
3. 模块级
4. 默认 `vault`

### 各模块货币配置

- `SystemShop`
  - 支持商品级 `currency`
  - 支持 shop 级 `Currency.Key`
  - 支持模块级 `Currency.Key`
- `PlayerShop`
  - 支持 shop 级
  - 支持模块级
- `GlobalMarket`
  - 支持 shop 级
  - 支持模块级
- `Auction`
  - 支持 shop 级
  - 支持模块级
- `Transaction`
  - 支持 shop 级
  - 支持模块级
- `ChestShop`
  - 只支持模块级
- `Cart`
  - 不配置业务货币
- `Record`
  - 不配置业务货币

## Bindings 规则

`Bindings.Commands` 可包含：

- `Bindings`
- `Register`
- `Show-In-Help`
- `Priority`
- `Condition`
- `Help`
- `Help-Key`
- `Hint-Keys`

其中：

- `Condition` 是 Kether 动作字符串
- `Help` 是多行帮助内容
- 支持 `{command}`、`{binding}`、`{shop-id}`、`{shop}` 等变量

## SystemShop 商品规则

商品支持：

- `material`
- `item`
- `amount`
- `price`
- `buy-max`
- `name`
- `lore`
- `currency`

如果生成的是高保真商品定义，优先输出 `item` 语义对应的结构说明，并同时保留当前 MatrixShop 支持的字段。

当前推荐结构：

- 商品本体放在 `SystemShop/goods/<product-id>.yml`
- 分类文件 `SystemShop/shops/<shop-id>.yml` 里的 `goods:` 只写商品 id 列表
- `shops/*.yml` 里直接内联 `goods.<id>` 仍兼容，但不应作为新配置默认写法

## 管理员商品维护

SystemShop 当前支持管理员快速维护商品：

- `/matrixshopadmin goods ui [page]`
- `/matrixshopadmin goods save <price> [buy-max] [product-id]`
- `/matrixshopadmin goods add <category> <product-id>`
- `/matrixshopadmin goods select <category> <product-id>`
- `/matrixshopadmin goods edit <price|buy-max|currency|name|item|remove> ...`

这属于后台命令，不应把它写成配置字段。

## 输出要求

当 AIChat 根据本知识库生成配置时，应遵守：

1. 先给出目标文件路径
2. 再给出完整 YAML
3. 不发明插件当前不支持的键
4. 如果需求是旧配置迁移，直接转成当前 MatrixShop 命名和目录结构
