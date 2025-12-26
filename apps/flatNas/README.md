# FlatNas — 精简说明

FlatNas 是一个轻量级且可定制的个人导航页与仪表盘系统（Vue3 + Express），适合 NAS 和家庭服务器场景，内置文件传输、小组件、书签与播放器。

主要特性：
- 可拖拽的仪表盘与可配置的小组件（文件传输、RSS、书签、音乐播放器等）
- 内置文件传输助手和数据持久化（`server/data/data.json`）
- 支持 Docker 部署和一键安装脚本，建议挂载数据目录以保证持久化

快速部署（示例）：
```bash
docker pull qdnas/flatnas:latest
docker run -d -p 23000:3000 -v ./server/data:/app/server/data --name flatnas qdnas/flatnas:latest
```

注意事项：
- 默认初始密码 `admin`，首次登录后请修改
- 挂载 `server/data`、`server/doc`、`server/music` 等目录以避免数据丢失

上游仓库：https://github.com/Garry-QD/FlatNas
