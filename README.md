# AI 协作规范仓库

[English](README.en.md) · [简体中文](README.md)

跨项目、跨 Agent 的规范与交接中枢。目标是让 DSH / Trae / WorkBuddy 这类上下文彼此隔离的 Agent，通过**仓库里的文件**而非聊天记忆协作。

> **仓库边界**：本仓库只包含**规范本体**，可公开。`projects/` 下的项目现场手册属于独立项目，**已 gitignore，不随本仓库上传**。

## 设计原则

1. **仓库是唯一事实源**：Agent 不共享记忆，只共享文件。任何交接都必须落盘成 commit。
2. **两层规则**：根目录 `AGENTS.md` 是全局习惯（薄）；项目现场手册（厚）由各项目自己的仓库维护，不属于本仓库。Agent 自动读取最近的一份。
3. **规格先行**：写代码前先有 `spec.md` → `plan.md` → `tasks.md`，人拍板后再进入实现。
4. **最小改动**：只改任务相关部分，不重构无关代码，不用臆测的功能堆砌。
5. **完成可验证**：每个任务有可自检的成功标准；未验证不叫完成。
6. **上下文是有限资源**：一任务一会话、精准读、输出克制、保护缓存；脏上下文既费钱又让模型变笨（见 `skills/09`）。

## 目录结构

```
.
├── AGENTS.md                         全局规则（所有项目通用）
├── README.md                         中文主说明（本文件）
├── README.en.md                      英文精简版（门面，细节指回中文）
├── CHANGELOG.md                      版本日志
├── CONTRIBUTING.md                   规范迭代约定
├── llms.txt                          给 Agent 的入口索引（可选，对接网站时）
├── .github/workflows/validate-links.yml  相对链接与命名校验
├── specs/_template/                  规格驱动模板
│   ├── spec.md / plan.md / tasks.md / decision.md
│   └── current-solution-statement.md 「当前生效方案」唯一事实源（最高优先级）
├── skills/                           可复用工作流（agent 按需加载）
│   ├── 01-requirements-clarification.md
│   ├── 02-spec-writing.md
│   ├── 03-task-breakdown.md
│   ├── 04-implementation-self-check.md
│   ├── 05-handoff-retrospective.md
│   ├── 06-cross-project-sync.md      功能级核对（非文件级）
│   ├── 07-verification-layers.md     静态 / 文档 / 真机三层
│   ├── 08-config-secrets.md          单一事实源 + 分层 + fail-closed
│   └── 09-context-token-efficiency.md 一任务一会话 + 精准读 + 缓存保护
└── handoff/                          跨 agent 交接协议
    ├── PROTOCOL.md                   交接规则
    └── HANDOFF.md                    当前交接状态（活文档）

[projects/]                           项目现场手册 — 本地保留，已 gitignore，独立项目另传
```

> `.gitignore` 明确排除 `projects/`。CI 会检查它未被意外追踪。

## 从自己项目提炼的九条共性（已写进规范）

1. 「当前方案唯一声明」缺失是最大痛点 → 模板 `specs/_template/current-solution-statement.md`
2. 功能级核对取代文件级核对 → `skills/06`
3. 每个领域单一事实源，文档/UI/代码从它派生 → `skills/08`
4. 密钥/配置分层与 fail-closed → `skills/08`
5. AI 协作规则文件已有雏形但分散 → 本仓库的 `AGENTS.md` 统一收口
6. 人做最后一步：AI 不启服务、不做真机 → `skills/07`
7. 静态验证优先于运行时验证 → `skills/07`
8. 上下文卫生等同代码卫生：一任务一会话、精准读、保护缓存 → `skills/09`（DSH 会话复盘 + 官方成本模型）
9. 部署约定高度重复（宝塔/子路径/端口/crontab）→ 待补 `skills/10`

## 使用流程

```
需求 → 定标准（问清判断口径）→ 定结构（拍板骨架）
     → 定机制（配置/版本/迁移）→ 小步实施（每轮自校验）
     → 验收沉淀（变更清单 + 决策记录）
```

具体到多 Agent 联动：

```
DSH（调研 / 架构 / 规格）──写 spec.md + plan.md ──▶ git commit
Trae（编码 / 重构 / 调试）──读 spec/plan，写代码 ──▶ git commit
WorkBuddy（文档 / 验收 / 规范沉淀）──读代码与 commit ──▶ git commit
```

每个 Agent 开工第一步：读 `AGENTS.md` + `handoff/HANDOFF.md`（项目仓库再读该项目的现场手册）；完成后更新 `HANDOFF.md` 并提交。

## 仓库

- **地址**：`https://github.com/chuliuLiu/ai-collab-playbook`
- **默认分支**：`main`
- **可见性**：Public（仓库内只有规范本体，无项目敏感信息）
- **CI**：每次 push 自动校验三项——文件名全小写 kebab-case、Markdown 相对链接可解析、`projects/` 未被追踪

新 Agent 接入：克隆仓库 → 读 `AGENTS.md` + `handoff/HANDOFF.md` → 按 `skills/` 执行 → 更新 `HANDOFF.md` 并提交。

## 发布前检查清单

- [ ] `git ls-files projects/` 输出为空（CI 也会拦截）
- [ ] 无密钥、token、真实账号、客户信息、私有聊天记录
- [ ] 两版 README 互链有效；冲突时以中文版为准
- [ ] LICENSE 授权类型已定（当前未添加）

## 状态

- [x] 全局规则与目录骨架
- [x] 规格 / 决策 / 当前方案声明模板
- [x] 九个 skills 工作流（09 = 上下文与 Token 效率）
- [x] 七项目共性已提炼为规范（现场手册本体不入库，独立项目另传）
- [x] GitHub 就绪：英文门面 / 变更日志 / 贡献约定 / llms.txt / CI 校验 / kebab-case / projects 忽略
- [ ] 部署与运维规范（skills/10）
- [ ] 首个实操项目验证
