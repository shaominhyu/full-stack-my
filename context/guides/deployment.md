# 生产部署从哪里开始？

适用于本仓库的 FastAPI Cloud 和自托管 Docker Compose 发布。本机启动、停止服务和查看开发数据库，请查运维手册的「本地启动」和「查看和操作本地数据库」。

| 部署目标 | 当前入口 | 核验 |
| --- | --- | --- |
| FastAPI Cloud | 按云部署手册配置应用、外部 PostgreSQL 和部署凭据，在 GitHub Actions 手动运行 `Deploy`。 | 查看该次运行的构建、准备数据库和部署步骤，再打开云端应用地址及其 `/docs`。 |
| 自托管服务器 | 按自托管手册准备服务器和域名。通过 GitHub Actions 发布时，手动运行 `Deploy with Docker Compose`，任务在服务器的自托管 Runner 执行。 | 核对选中的是自托管工作流，检查它的运行结果，再打开目标域名及其 `/docs`。 |

接手「合并后没有发布」时，先查工作流的触发事件。[Cloud 部署触发方式的变更经过](../questions/cloud-deploy-trigger.md)

工作流改名、更换触发事件或执行环境时，复查表中对应的入口和核验方法。

## 核对来源

- [运维手册](../../docs/operations.md) <!-- sha256:5502fd5a7cda713d02401535d49d25590452270bb637d74c536416807d8b953b -->
- [FastAPI Cloud 部署手册](../../deployment.md) <!-- sha256:b5919fe06e5b7a07068a7a0301876c961277e75d0c2dcb65013579d72bf6561c -->
- [Cloud 发布工作流](../../.github/workflows/deploy.yml) <!-- sha256:b50a15ba99649e3c32b5c7274500b3b665efbf1f6dc16cf4b44c1387c8b85387 -->
- [自托管 Compose 部署手册](../../deployment-docker-compose.md) <!-- sha256:f5e5683fdfd7ae34fac04f3ef0895caf65761e32eaa66b794a140a4f330e0f5c -->
- [自托管发布工作流](../../.github/workflows/deploy-docker-compose.yml) <!-- sha256:32792e14027139ac1d81b611d6dcc616ccfb6c9ca92854d276ec5e02b197363d -->
