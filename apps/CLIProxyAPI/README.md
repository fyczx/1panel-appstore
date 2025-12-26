# CLIProxyAPI — 简介

CLIProxyAPI 是一个代理服务器，为 CLI 工具和 IDE 提供与 OpenAI/Gemini/Claude/Codex 兼容的 API 接口。它允许你通过统一的接口使用多个上游模型和订阅。

## 主要特性

- **多模型支持**：OpenAI、Gemini、Claude、Codex 兼容的 API 端点
- **OAuth 认证**：支持 Claude Code、Codex、Qwen Code、iFlow 等工具的 OAuth 登录
- **高级功能**：流式响应、函数调用、多模态输入（文本和图片）
- **负载均衡**：多账户轮询负载均衡（Gemini、OpenAI、Claude、Qwen、iFlow）
- **安全设计**：管理 API 默认仅限 localhost 访问
- **IDE 集成**：Amp CLI 和其他 IDE 扩展支持与提供商路由

## 快速部署

使用 Docker 快速部署：

```bash
docker run -d \
  -p 8317:8317 \
  -v $(pwd)/config.yaml:/CLIProxyAPI/config.yaml \
  -v $(pwd)/auths:/root/.cli-proxy-api \
  -v $(pwd)/logs:/CLIProxyAPI/logs \
  --name cli-proxy-api eceasy/cli-proxy-api:latest
```

## 重要说明

- 需要在 `config.yaml` 中配置上游服务商的凭证
- 管理端点默认仅限 localhost 访问（`127.0.0.1:8085`）
- 支持自定义 Docker 镜像版本，通过环境变量 `CLI_PROXY_IMAGE_REPO` 和 `CLI_PROXY_IMAGE_TAG` 指定

## 挂载目录说明

应用会挂载以下目录：

- `/CLIProxyAPI/config.yaml`：主配置文件（需要提前准备）
- `/root/.cli-proxy-api`：OAuth 凭证和认证信息存储目录
- `/CLIProxyAPI/logs`：应用日志目录

## 官方资源

- **项目地址**：https://github.com/router-for-me/CLIProxyAPI
- **官方文档**：https://help.router-for.me/
- **管理 API 文档**：https://help.router-for.me/management/api
- **SDK 文档**：参考项目仓库中的 `docs/` 目录

## 配置建议

部署后，可通过本地管理界面（`http://127.0.0.1:8085`）配置提供商和模型映射。
