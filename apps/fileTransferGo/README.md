# File Transfer Go — 精简说明

文件快传（File Transfer Go）是一个基于 WebRTC 的 P2P 文件/文字传输与桌面共享工具，后端为 Go，前端为 Next.js；数据端到端不经服务器（可选 TURN 支持）。

主要特性：
- WebRTC DataChannel P2P 传输（端到端加密）
- 支持多文件、文字传输、桌面共享与断点续传
- 提供 Docker Compose、单二进制与开发模式部署

快速部署（示例）：
```bash
git clone https://github.com/MatrixSeven/file-transfer-go.git
cd file-transfer-go
docker-compose up -d
# 或 docker run -d -p 8080:8080 matrixseven/file-transfer-go:latest
```

配置要点：
- 常用环境变量：`PORT`、`GO_BACKEND_URL`、TURN/STUN 设置
- 若部署在 NAT/受限网络，建议配置 TURN 服务

上游仓库：https://github.com/MatrixSeven/file-transfer-go
