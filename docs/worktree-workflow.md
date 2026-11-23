# Worktree 开发流程

## 分支与目录命名

- 分支用 `<类型>/<任务短名>`，例如 `feat/items-filter`、`fix/login-redirect` 或 `docs/worktree-naming`。
- worktree 统一放在主目录的 `worktrees/` 下，目录名用 `fullstack-<类型>-<任务短名>`。例如 `feat/items-filter` 对应 `worktrees/fullstack-feat-items-filter`。
- 任务短名用小写英文，单词用连字符连接。有 Issue 编号时可以放在短名前，例如 `fix/42-login-redirect`。

## 创建或复用工作树

先用 `git worktree list` 查看已有工作树。找到当前任务的工作树就直接进入。新任务在主工作目录里从最新的目标分支创建工作树。以下以 GitHub `master` 为例。

```bash
git fetch github master
mkdir -p worktrees
git worktree add -b feat/items-filter worktrees/fullstack-feat-items-filter github/master
cd worktrees/fullstack-feat-items-filter
```

将示例的任务名换成本次改动。目标仓库是 Gitee 时，用 `origin` 作为远程、`origin/master` 作为基线。

主目录的 Git 忽略规则覆盖整个 `worktrees/`，任务改动从对应的工作树里提交。

## 提交和合并

完成提交前检查后，在任务分支提交，用 `git push -u github HEAD` 推送，然后提 PR 合入 `master`。目标仓库是 Gitee 时，推送到 `origin` 并在该仓库提 PR/MR。[提交前检查](quality-checks.md)
