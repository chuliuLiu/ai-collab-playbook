# Skill 08 · 配置与密钥管理规范

**何时用**：新建项目、改配置结构、加密钥相关代码。

## 单一事实源

每个领域有且仅有一个事实源，文档 / UI / 代码从它派生。实例：

- xiaozhi-oneclick：`data/settings.json` 是唯一配置来源。
- Emotion-Lab：调参只改 `data/*.json`，算法里出现硬编码权重视为破坏承诺。
- blockly-linkdog：`getCatalog` 唯一真相源是 `blocks.js`，`help()` 与 UI 面板共用同一份模板常量。
- dsh-linkdog-pet：`scripts/mock_device.mjs` 是可执行的协议参考实现。

## 分层与优先级

```
环境变量 > config_secret.json > config.json > 默认值
```

- `config.json`：非机密，随代码同步。
- `config_secret.json`：机密，仅服务端本地，已 gitignore。
- 所有密钥 / token / PAT 不硬编码、不提交、日志不打印原文。

## Fail-closed

- 未设 `ADMIN_TOKEN` → 默认 403。
- 默认弱口令（如 `123_789`）必须替换才算部署完成。
- 发布包不含任何人的 Key / 配置 / 聊天数据，无遥测、无账号。

## 向后兼容

- 可选字段禁止 NULL 覆盖，用 COALESCE / 默认值兜底。
- 数据结构会变就第一天设计版本号 + 迁移，不要靠换存储 key 补漏。
- 配置版本化：配置自带 schemaVersion，加载时按版本迁移。

## 反例

- 把 AU 角度塞进给 LLM 的情绪维度 → LLM 基本废掉（Emotion-Lab §5.1）。
