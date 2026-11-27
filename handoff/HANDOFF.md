## 当前阶段
规范仓库 v1.1.0 · GitHub 就绪（双语门面 + kebab-case 命名 + CI 校验）

## 负责 Agent
WorkBuddy

## 已完成
- 目录骨架：AGENTS.md / README.md / specs / skills / handoff（projects/ 已忽略，独立项目另传）
- 全局规则 AGENTS.md（七条，新增「上下文纪律」）
- 跨 Agent 交接协议 PROTOCOL.md
- 五个模板（含从项目提炼的「当前方案声明」）
- 九个 skills 工作流（06~08 来自跨项目共性提炼，09 = 上下文与 Token 效率）
- 规范 v1.1：吸收 DSH 会话复盘 + Anthropic 官方成本模型，修正「每轮全价重付」的缓存盲区
- GitHub 就绪：全文件 kebab-case 重命名；新增 README.en.md / CHANGELOG.md / CONTRIBUTING.md / llms.txt / .gitignore / CI 校验（链接 + 命名 + projects 未追踪）；规范本体可公开

## 进行中
- 无（本轮新增 `skills/09`，已接入全局规则与仓库索引）

## 阻塞 / 待确认
- 平台已定 GitHub；仓库名 `ai-collab-playbook`，主分支 `main`，可设为 Public
- 仓库边界已定：只传规范本体；`projects/` gitignore，作为独立项目另传
- 首个试跑项目选哪个（建议 xiaozhi-oneclick 快速闭环 或 dsh-linkdog-pet 验证多 agent）
- 两个文件未读取（敏感内容审批超时）：LinkDogDM/AGENTS.md、xiaozhi-oneclick/交接_20261108.md，需授权后补录

## 下一步 Agent 必读
1. 先读根目录 `AGENTS.md` 与 `handoff/PROTOCOL.md`
2. 项目现场手册不在本仓库，在对应项目仓库中就近优先
3. 共性规范在 `skills/06`（同步）/`07`（验证）/`08`（配置密钥）/`09`（上下文与 Token 效率）
4. 新会话第一句只给：目标 + 本文件路径 + 当前阻塞；不要复述历史
5. 任何阶段改动后更新本文件并 commit
