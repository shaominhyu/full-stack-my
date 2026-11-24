# 为什么合入 master 后没有触发 FastAPI Cloud 部署？

查找线索包括「合并后没有发布」「Actions 没有 Deploy 记录」和「推送 master」。适用于本仓库的 FastAPI Cloud 工作流。已核对工作流配置、部署手册和变更提交。

## 下次先查什么

1. 打开目标版本的 Cloud 发布工作流，查看 `on`。当前只声明 `workflow_dispatch`，合并后不会自动产生一条 `Deploy` 运行记录。
2. 目标是发布时，按部署手册在 GitHub Actions 手动运行 `Deploy`。如果已经有运行记录，打开该次详情，按实际失败步骤继续排查。[生产部署入口](../guides/deployment.md)

## 这个判断怎么来的

2026-11-20，提交 `d5eed86` 移除了向 `master` 推送时的自动发布触发条件，保留了手动入口，并同步修改了部署说明。此前仅修改 `release-notes.md` 的推送已被排除。沿用旧流程等待合并后自动发布，会把正常的触发行为误当成故障。[原始变更](https://github.com/shaominhyu/full-stack-my/commit/d5eed86a0604ade676399c991c35f9ca8e0cbeda)

可在仓库运行 `git show d5eed86 -- .github/workflows/deploy.yml deployment.md` 核对旧条件与替换内容。工作流的触发事件再次变化时，更新上面的排查起点并保留这段历史。

## 核对来源

- [当前 Cloud 发布工作流](../../.github/workflows/deploy.yml) <!-- sha256:b50a15ba99649e3c32b5c7274500b3b665efbf1f6dc16cf4b44c1387c8b85387 -->
- [当前 Cloud 部署手册](../../deployment.md) <!-- sha256:b5919fe06e5b7a07068a7a0301876c961277e75d0c2dcb65013579d72bf6561c -->
