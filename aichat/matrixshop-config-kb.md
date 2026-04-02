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

`SystemShop/goods/*.yml` 还可以定义两类可复用资源：

- `Kind: group`
- `Kind: pool`

其中：

- `group` 用于复用一组商品 id
- `pool` 用于刷新区域的加权随机候选

## SystemShop 刷新规则

刷新配置应写在：

- `SystemShop/shops/<shop-id>.yml`
- `icons.<char>.refresh`

当前可用结构包括：

- `Enabled`
- `Cron`
- `Timezone`
- `Same-For-Players-In-Group`
- `groups.<id>.Enabled`
- `groups.<id>.Match-Script`
- `groups.<id>.Random-Refresh`
- `groups.<id>.Pick`
- `groups.<id>.Pool-Ref`
- `groups.<id>.goods`

其中：

- `Pool-Ref` 指向 `Kind: pool` 的 goods 资源
- `goods` 可直接引用商品或 `Kind: group` 资源
- `Match-Script` 用于按玩家条件分组

默认资源中还存在这三份后台 UI 文件：

- `SystemShop/ui/goods-browser.yml`
- `SystemShop/ui/goods-editor.yml`
- `SystemShop/ui/goods-shops.yml`

## 管理员商品维护

SystemShop 当前支持管理员快速维护商品：

- `/matrixshopadmin goods ui [page]`
- `/matrixshopadmin goods save <price> [buy-max] [product-id]`
- `/matrixshopadmin goods add <category> <product-id>`
- `/matrixshopadmin goods select <category> <product-id>`
- `/matrixshopadmin goods edit <price|buy-max|currency|name|item|remove> ...`

这属于后台命令，不应把它写成配置字段。

SystemShop 当前也支持刷新后台命令：

- `/matrixshopadmin refresh list [category]`
- `/matrixshopadmin refresh run <category> [icon]`

这同样属于后台命令，不应把它写成配置字段。

## 当前兼容性事实

当用户问“支持哪个版本”或“兼容哪个服务端”时，应区分：

1. 已验证运行结果
2. 源码层构建事实

当前已验证结果：

- `MatrixShop 1.3.0` 在 `Paper 1.21.8` 上 smoke boot 通过，验证日期 `2026-04-02`
- `MatrixShop 1.3.0` 在 `Paper 1.21.11` 上 smoke boot 通过，验证日期 `2026-04-02`

当前源码层事实：

- 插件版本：`1.3.0`
- 构建目标：`Bukkit API 1.12.2`
- 必需依赖：`MatrixLib 1.0.1`

不要把未验证的 `Folia`、`Spigot`、`Bukkit` 或其他 Paper 版本直接写成“已验证兼容”。

## 输出要求

当 AIChat 根据本知识库生成配置时，应遵守：

1. 先给出目标文件路径
2. 再给出完整 YAML
3. 不发明插件当前不支持的键
4. 如果需求是旧配置迁移，直接转成当前 MatrixShop 命名和目录结构
