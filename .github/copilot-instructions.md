# Copilot 使用说明（为本仓库定制）

仓库概览
- 本仓库是一个基于 1Panel 的第三方 App Store：把每个应用放在 `apps/<app>/` 目录，版本在子目录（如 `0.9.0/`、`latest/`）。见 [README.md](README.md#L1-L20)。
- 每个应用通常包含两个层级的 `data.yml`：
  - 应用层 `apps/<app>/data.yml`：元数据模板与描述（参见 [apps/Template/data.yml](apps/Template/data.yml#L1-L20)）。
  - 版本层 `apps/<app>/<version>/data.yml`：包含 `formFields`、默认 envKey 等运行时配置（参见 [apps/Template/latest/data.yml](apps/Template/latest/data.yml#L1-L20)）。

主要约定（可直接采纳）
- 版本目录必须包含 `docker-compose.yml`（用于 1Panel 部署）和可选的 `data.yml`。示例：`apps/kvrocks/2.14.0/docker-compose.yml`。
- `data.yml` 中的表单字段使用 `formFields`，字段包含 `envKey`、`rule`、`default`、`labelZh/labelEn` 等。不要随意更改这些 key 名称，否则面板映射会失效。
- 应用文件夹名只能使用英文（用于 Linux 文件夹名），并在应用层 `data.yml` 的 `key` 字段对应。

开发者工作流要点
- 同步：仓库根有示例同步脚本（README 中示例），工作流是：`git clone` →（可选）运行 `mirror.sh` → 将选定的 `apps/` 目录复制到 1Panel 的本地 apps 目录。阅读同步脚本示例见 [README.md](README.md#L60-L110)。
- 镜像替换：仓库提供 `mirror.sh` 的约定用于替换 `docker-compose.yml` 中的镜像地址（配合 `/opt/mirror-config.env`）。不要在单个应用中把镜像替换逻辑混入其他配置文件。

常见模式与示例
- 表单字段映射示例（来自 Template）:

  - `envKey: PANEL_APP_PORT_HTTP` — 面板会把用户填写的端口映射到此环境变量，见 [apps/Template/latest/data.yml](apps/Template/latest/data.yml#L1-L20)。
- 版本命名以语义化版本或 `latest` 为主；CI 或发布流程会以目录名作为版本识别。

编辑与 PR 建议
- 修改应用时：只改对应 `apps/<app>/<version>/docker-compose.yml` 或该版本的 `data.yml`。若变更会影响 UI（新增/修改 formFields），必须同时更新版本 `data.yml`。
- 增加新应用：新建 `apps/<new-app>/data.yml`（填写 `key`、`name`、`tags`、`shortDescZh` 等），并至少创建一个版本目录包含 `docker-compose.yml` 与版本 `data.yml`。
- 保持向后兼容：若需要删除或重命名 `envKey`，请保留旧 key 的别名一段时间以避免现有安装失效。

代码审查关注点
- 确认 `data.yml` 的 `formFields` 是否使用已识别的 `rule`（例如 `paramPort`），以及 `envKey` 是否与 `docker-compose.yml` 中使用的环境变量一致。
- 检查 `docker-compose.yml` 中的镜像地址是否符合仓库的镜像替换约定（如会被 `mirror.sh` 替换），避免硬编码私有镜像地址。

查找示例文件
- 应用模板：[apps/Template/data.yml](apps/Template/data.yml#L1-L20)
- 模板版本示例：[apps/Template/latest/data.yml](apps/Template/latest/data.yml#L1-L20)
- 仓库说明：[README.md](README.md#L1-L20)

如果不清楚的地方
- 想让我把现有某个应用（例如 `apps/kvrocks`）的 `data.yml` 与 `docker-compose.yml` 解析成一个检查清单吗？回复要解析的应用名即可。

（结束）
