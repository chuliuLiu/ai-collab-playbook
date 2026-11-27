## 当前阶段
规范仓库已上线 GitHub `main` · 持续迭代中

## 负责 Agent
WorkBuddy

## 已完成
- 目录骨架：AGENTS.md / README 双版 / specs / skills / handoff / CHANGELOG / CONTRIBUTING / llms.txt / CI
- 全局规则 AGENTS.md（七条，含「上下文纪律」）
- 跨 Agent 交接协议 PROTOCOL.md
- 五个模板（含从项目提炼的「当前方案声明」）
- skills 工作流（跨项目共性 06~08、Token 效率 09、commit review 与合并 10）
- GitHub 已推送：`chuliuLiu/ai-collab-playbook`，Public，main 分支；CI 校验链接 / 命名 / projects 未追踪
- 仓库边界：只传规范本体；`projects/` gitignore，作为独立项目另传

## 进行中
- 无

## 阻塞 / 待确认
- 首个试跑项目选哪个（建议 xiaozhi-oneclick 快速闭环 或 dsh-linkdog-pet 验证多 agent）
- 两个文件未读取（敏感内容审批超时）：LinkDogDM/AGENTS.md、xiaozhi-oneclick/交接_20261108.md，需授权后补录

## 下一步 Agent 必读
1. 先读根目录 `AGENTS.md` 与 `handoff/PROTOCOL.md`
2. 项目现场手册不在本仓库，在对应项目仓库中就近优先
3. 共性规范在 `skills/06`（同步）/`07`（验证）/`08`（配置密钥）/`09`（Token 效率）/`10`（commit 评审与合并）
4. 合并 AI commit 前必走 `skills/10` 的范围→意图→测试→行为四步；合并决定由人做
5. 新会话第一句只给：目标 + 本文件路径 + 当前阻塞；不要复述历史
6. 任何阶段改动后更新本文件并 commit
