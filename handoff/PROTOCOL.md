# 跨 Agent 交接协议

## 核心问题

DSH、Trae、WorkBuddy 的上下文记忆彼此独立——上一个 Agent 聊过的细节，下一个完全不知道。
解决方式不是"把聊天记录贴过去"，而是**把状态落盘成文件，用 git commit 作为交接动作**。

## 交接三要素

每次交接必须包含：

1. **做了什么**：本次 commit 的改动范围（文件 + 一句话说明）。
2. **验证结果**：跑了什么命令、通过没通过、有没有遗留。
3. **下一步**：给接手 Agent 的具体提示（先读哪个文件、注意什么坑、不要碰什么）。

## 状态文件

`handoff/HANDOFF.md` 是活文档，格式：

```markdown
## 当前阶段
[调研 / 规格 / 实现 / 验收 / 完成]

## 负责 Agent
[DSH / Trae / WorkBuddy]

## 已完成
- ...

## 进行中
- ...

## 阻塞 / 待确认
- ...

## 下一步 Agent 必读
1. ...
```

## 流程

```
Agent A 开工
  → 读 AGENTS.md + 项目 AGENTS.md + HANDOFF.md
  → 改文件 / 写代码
  → 更新 HANDOFF.md（写清三步要素）
  → git commit（一个阶段一个 commit）
  → 通知人 / 触发 Agent B

Agent B 开工
  → 从 HANDOFF.md 和 git log 恢复上下文
  → 不需要 A 的聊天记录
```

## 给各 Agent 的分工建议

| Agent | 擅长 | 适合阶段 |
|---|---|---|
| DSH | 调研、架构、规格生成 | 定标准 / 定结构 / 定机制 |
| Trae | 编码、重构、调试 | 小步实施 |
| WorkBuddy | 文档、验收、规范沉淀 | 验收沉淀 / 跨项目抽象 |

## 防坑

- 不要同时两个 Agent 改同一文件——用分支或严格串行。
- 交接前必须 commit，否则下一个 Agent 读到的还是旧状态。
- HANDOFF.md 只写"状态"，不写"过程复盘"；复盘放 `docs/`。
