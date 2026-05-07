# Skill: session-status-manager（会话状态管理）

## 何时触发
- 用户提到：当前写到哪里、上次写作进度、跨会话续写、项目状态

## 目标
- 维护唯一实时状态文件
- 追加历史快照，支持跨会话恢复

## 读取文件
- `status/current_status.md`
- `status/history/`
- `logs/status_history.json`
- `logs/mutations.jsonl`

## 执行步骤
1. 基于最新章节/时间线更新 `current_status.md`。
2. 生成带时间戳的历史快照到 `status/history/`。
3. 追加更新索引 `status_history.json`。
4. 返回“下一会话开写上下文”。

## 输出格式
- 行动清单
- 补丁文本（current + history + index）
- 风险说明（状态字段缺失）
