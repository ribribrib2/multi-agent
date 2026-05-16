# 团队贡献指南

## 重要约定

- **所有输出文档必须使用中文**。无论是代码注释、文档、规范说明还是沟通内容，统一使用中文书写。
- **所有交付物必须提交到 GitHub**。如果不在仓库里，就不算存在。
- **每个 Agent 开始工作前，必须读取本仓库中的所有规范文档**（CONTRIBUTING.md、CODING_STANDARDS.md、ALIGNMENT.md），并严格遵守其中的规则。

## 分支策略

- **`main`**：生产就绪的代码。只能通过 PR 合并进入，禁止直接推送。
- **`agent/agent/<hash>`**：Agent 工作区分支，由 Multica 自动创建。禁止直接合并。
- **功能分支**：`feature/<简短描述>`，供人类贡献者使用。

### 工作流程

1. 从 `main` 拉取最新代码，创建功能分支。
2. 频繁提交，使用清晰的提交信息。
3. 准备好后创建 PR 到 `main`，等待 review。
4. 使用 Squash Merge 保持历史整洁。

## 提交信息规范

遵循 [Conventional Commits](https://www.conventionalcommits.org/)：

```
<类型>[可选 范围]: <描述>

[可选 正文]

[可选 脚注]
```

类型：`feat`（新功能）、`fix`（修复）、`docs`（文档）、`style`（格式）、`refactor`（重构）、`test`（测试）、`chore`（杂务）、`ci`（持续集成）

示例：
```
feat(auth): 添加 JWT token 刷新接口
fix(api): 处理用户偏好为 null 的情况
docs: 添加贡献指南
```

## 所有输出提交到 GitHub

**每个团队成员（人类或 Agent）必须将其产出提交到本仓库。**

- Agent 的代码变更提交到工作区分支，然后通过 PR 合并到 `main`。
- Agent 产出的文档、规范、设计文档等，通过 PR 提交到 `main`。
- **禁止**将交付物仅留在 issue 评论或运行日志中。如果不在仓库里，就不算存在。
- Issue 评论仅用于协调和状态更新。仓库是唯一的真实来源。

### 输出物清单

| 类型 | 交付物 | 位置 |
|------|--------|------|
| 代码 | 源文件、测试、配置 | `src/`、`tests/` 等 |
| 文档 | 规范、指南、决策 | `docs/` 或仓库根目录 |
| 配置 | 构建、lint、CI、Docker | 仓库根目录或 `.github/` |
| 设计 | 架构图、RFC | `docs/design/` |
| 数据 | 迁移脚本、fixtures | `migrations/`、`fixtures/` |

## PR 要求

- **合并到 `main` 前至少需要一次人类 review**（初始草案阶段 Agent 之间的 review 可接受）。
- PR 描述必须解释**为什么**，不仅仅是做了什么。
- 引用相关 issue（例如 "Closes #4"）。
- CI 检查必须通过（设置 CI 后）。

## Issue 管理

- 使用 Multica 平台进行 issue 跟踪。
- 提交信息和 PR 中引用 issue ID：`[MUL-123]` 或 `[AIW-4]`。
- PR 准备好后，将 issue 状态更新为 `in_review` 或关闭。
