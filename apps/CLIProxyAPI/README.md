# CLIProxyAPI — 精简说明

CLIProxyAPI 提供与 OpenAI/Gemini/Claude/Codex 兼容的本地代理 API，适合将多个上游模型/订阅通过统一接口暴露给 CLI 客户端和工具链。

要点：
- 支持 OAuth、多账户轮询、流式响应与函数调用
- 管理端点默认仅限 localhost（安全为先）
- 提供可选的 Docker 部署与配置示例

快速部署示例（Docker）：
```bash
# 使用默认镜像
docker run -d \
	-p 8317:8317 -p 8085:8085 \
	-v $(pwd)/config.yaml:/CLIProxyAPI/config.yaml \
	-v $(pwd)/auths:/root/.cli-proxy-api \
	-v $(pwd)/logs:/CLIProxyAPI/logs \
	--name cli-proxy-api eceasy/cli-proxy-api:latest
```

更多配置、SDK 文档与管理 API，请参阅上游文档：
https://github.com/router-for-me/CLIProxyAPI