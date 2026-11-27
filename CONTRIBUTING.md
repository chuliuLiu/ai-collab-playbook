# 规范迭代约定

这份仓库本身也是一个项目，按 `AGENTS.md` 的规则迭代。

## 改什么

- 新增规范：先在 `skills/` 加文件，再挂到 `README.md`、`llms.txt` 索引和必要的 `AGENTS.md` 条目（CI 会校验索引完整性）。
- 改已有规范：更新正文 + `CHANGELOG.md`；如果改变了行为约束，版本号递增。
- 项目现场手册不属于本仓库（`projects/` 已 gitignore），在各自项目仓库维护；只写可验证的现状，不写计划或猜测。

## 命名

- 所有文件与目录：全小写 kebab-case，ASCII 字符，不用空格和中文。
- Agent 可直接读取的入口文件保持标准名：`AGENTS.md` / `README.md` / `llms.txt` / `CHANGELOG.md` / `CONTRIBUTING.md`。
- 标识符（API 名、环境变量、CLI 参数、协议字段、错误码）保留原文，不翻译。

## 提交

- Conventional Commits：`<type>(<scope>): <做了什么>`，例如 `docs(skills): 增加上下文与 Token 效率规范`。
- 一个阶段一个 commit，便于追溯每一步改了什么、由谁验证。
- 不要提交密钥、token、真实账号、客户信息、私有聊天记录。

## 版本

- 语义化版本：约束变化升 minor，结构/破坏性调整升 major，措辞修正升 patch。
- 每次改完在 `CHANGELOG.md` 记一条；版本历史只维护在这一处，不在 skill 或 README 中复述进度。

## 发布前

本仓库只含规范本体，可公开。提交前确认 `git ls-files projects/` 为空、`projects/` 仍在 `.gitignore` 中（CI 会强制校验）。
