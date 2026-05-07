# `status/` 说明

小说运行态目录。

- `current_status.md`：唯一实时状态文件
- `history/`：追加式历史快照（每次提交后生成）

用途：跨会话续写与状态回放。

## 操作指引
1. 每次 commit 后立即更新 `current_status.md`。
2. 同时在 `history/` 生成带时间戳的快照。
3. 状态摘要必须写清当前 Arc、Chapter 和主线推进。
4. 状态索引同步更新 `logs/status_history.json`。
