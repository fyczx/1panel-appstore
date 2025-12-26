(The file `e:\github\1panel-appstore\apps\decoTV\README.md` exists, but is empty)
# DecoTV — 精简说明

DecoTV 是一个基于 Next.js 的影视聚合播放器（开箱即用的前端与管理后台），不包含播放源：部署后需在管理后台配置外部数据源（API/站点）。

主要特性：
- 多源聚合搜索与详情页（支持 Apple CMS V10 格式）
- HLS 播放（ArtPlayer / HLS.js）、收藏与观看记录
- 多种存储支持：kvrocks / redis / upstash（推荐 kvrocks）
- 可选用户注册与 PWA 支持

快速部署（示例）：
```bash
docker pull ghcr.io/decohererk/decotv:latest
docker run -d -p 3000:3000 --name decotv ghcr.io/decohererk/decotv:latest
```

注意事项：
- 部署后必须在管理后台填写或导入播放源/接口配置，项目本身不提供播放源。
- 请设置管理员账号密码并谨慎开放公网访问。

上游仓库：https://github.com/Decohererk/DecoTV
