# Phira MP NodejsVer - 插件索引

本仓库包含 Phira MP NodejsVer 服务器的插件索引，列出所有官方维护的插件及其仓库链接。

## 插件列表

| 插件 | 仓库链接 | 说明 |
|------|---------|------|
| WebSocket Support | `git@github.com:chuzouX/phira-mp-nodejsver-websocket.git` | WebSocket 实时通信支持 |
| Web Dashboard | `git@github.com:chuzouX/phira-mp-nodejsver-web-dashboard.git` | Web 管理面板 |
| NoneBot Auth | `git@github.com:chuzouX/phira-mp-nodejsver-nonebot-auth.git` | 基于密钥的管理员鉴权 |
| Room Announcer | `git@github.com:chuzouX/phira-mp-nodejsver-room-announcer.git` | 房间列表实时播报 |
| Tournament | `git@github.com:chuzouX/phira-mp-nodejsver-tournament.git` | 排行榜模式比赛插件 |

## 插件加载顺序

1. **WebSocket Support** - 基础通信层（无依赖）
2. **Web Dashboard** - Web UI 面板（依赖 websocket）
3. **NoneBot Auth** - 管理员鉴权（依赖 web-dashboard）
4. **Room Announcer** - 房间播报（依赖 websocket）
5. **Tournament** - 比赛系统（无依赖）

## 许可证

MIT License
