# Phira MP NodejsVer - 插件索引

本仓库包含 Phira MP NodejsVer 服务器的插件索引，列出所有官方维护的插件及其仓库链接。

## 插件列表

| 插件              | 仓库链接                                                         | 说明                         | 最新版本 |
| ----------------- | ---------------------------------------------------------------- | ---------------------------- | -------- |
| WebSocket Support | `git@github.com:chuzouX/phira-mp-nodejsver-websocket.git`        | WebSocket 实时通信支持       | v1.2.1   |
| Web Dashboard     | `git@github.com:chuzouX/phira-mp-nodejsver-web-dashboard.git`    | Web 管理面板                 | v1.7.0   |
| Room Announcer    | `git@github.com:chuzouX/phira-mp-nodejsver-room-announcer.git`   | 房间列表实时播报             | v1.5.0   |
| Titles            | `git@github.com:chuzouX/phira-mp-nodejsver-titles.git`           | 称号系统（擂主+累计）        | v1.0.0   |
| Federation        | `git@github.com:chuzouX/phira-mp-nodejsver-federation.git`       | 对等联邦节点管理，多服务器联机 | v1.0.0   |
| Server Control    | `git@github.com:chuzouX/phira-mp-nodejsver-server-control.git`   | 独立运维面板，指标与配置管理   | v1.0.0   |
| NoneBot Auth      | `git@github.com:chuzouX/phira-mp-nodejsver-nonebot-auth.git`     | 基于密钥的管理员鉴权         | v1.1.0   |
| Tournament        | `git@github.com:chuzouX/phira-mp-nodejsver-tournament.git`       | 排行榜模式比赛插件           | v1.1.1   |

## 插件安装教程

### 方式一：Git Clone（推荐）

```bash
# 进入 plugins 目录
cd plugins

# 克隆插件仓库
git clone https://github.com/chuzouX/phira-mp-nodejsver-websocket.git websocket
git clone https://github.com/chuzouX/phira-mp-nodejsver-web-dashboard.git web-dashboard
git clone https://github.com/chuzouX/phira-mp-nodejsver-room-announcer.git room-announcer
git clone https://github.com/chuzouX/phira-mp-nodejsver-titles.git titles
git clone https://github.com/chuzouX/phira-mp-nodejsver-federation.git federation
git clone https://github.com/chuzouX/phira-mp-nodejsver-nonebot-auth.git nonebot-auth
git clone https://github.com/chuzouX/phira-mp-nodejsver-tournament.git tournament
git clone https://github.com/chuzouX/phira-mp-nodejsver-server-control.git server-control
```

### 方式二：下载 ZIP

1. 在插件仓库页面点击 **Code → Download ZIP**
2. 解压后将文件夹重命名为插件名
3. 放入 `plugins/` 目录

### 方式三：手动下载单个文件

适用于简单插件（无需编译、无额外依赖的 `.js` 文件）：

```bash
# 创建插件目录
mkdir -p plugins/my-plugin/res

# 下载 plugin.yaml 和 main.js 放入对应位置
# 插件将自动被服务端加载
```

### 安装后操作

插件放入 `plugins/` 后，有两种加载方式：

- **重启服务端** — 自动扫描 `plugins/` 并加载所有启用状态的插件
- **控制台命令** — 在服务端控制台输入 `/plugins install <插件名>` 热加载

### 启用 / 禁用插件

| 命令                        | 说明                              |
| --------------------------- | --------------------------------- |
| `/plugins install <name>`   | 安装并加载插件                    |
| `/plugins uninstall <name>` | 卸载插件（删除目录）              |
| `/plugins enable <name>`    | 启用已禁用的插件（移除 `!` 前缀） |
| `/plugins disable <name>`   | 禁用插件（添加 `!` 前缀）         |
| `/plugins reload [name]`    | 重载插件（不指定则重载全部）      |
| `/plugins list`             | 列出所有插件及状态                |
| `/plugins info <name>`      | 查看插件详细信息                  |

### 目录结构示例

```
plugins/
├── web-dashboard/          # Web 管理面板
│   ├── plugin.yaml
│   ├── config.default.yaml
│   └── res/
│       ├── main.js
│       └── public/
├── websocket/              # WebSocket 支持
│   ├── plugin.yaml
│   └── res/
│       ├── main.js
│       └── lib/
├── room-announcer/         # 房间播报
│   ├── plugin.yaml
│   └── res/
│       └── main.js
├── titles/                 # 称号系统
│   ├── plugin.yaml
│   └── res/
│       └── main.js
├── federation/             # 联邦节点管理
│   ├── plugin.yaml
│   ├── config.default.yaml
│   └── res/
│       ├── main.js
│       └── FederationManager.js
├── server-control/         # 运维控制面板
│   ├── plugin.yaml
│   └── res/
│       └── main.js
└── !disabled-plugin/       # 以 ! 开头 = 禁用状态，不会被加载
    └── plugin.yaml
```

### 依赖关系

插件间可能存在依赖关系，安装时需按顺序放入：

1. **WebSocket Support** — 基础通信层（无依赖）
2. **Web Dashboard** — Web UI 面板（依赖 websocket）
3. **Room Announcer** — 房间播报（依赖 websocket）
4. **Titles** — 称号系统（依赖 websocket）
5. **Federation** — 联邦节点管理（无依赖）
6. **Server Control** — 运维控制面板（无依赖）
7. **NoneBot Auth** — 管理员鉴权（依赖 web-dashboard）
8. **Tournament** — 比赛插件（无依赖）

### 手动安装 vs 包管理器

当前版本插件通过 Git 仓库分发，安装过程是**手动**的：

- 将插件文件放入 `plugins/` 目录
- 通过控制台命令或重启加载

未来版本计划支持自动化包管理器，实现一键安装。

## 许可证

MIT License
