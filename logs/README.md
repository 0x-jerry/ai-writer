# `logs/` 说明

审计日志目录（JSON / JSONL）。

## 文件职责
- `status_history.json`：状态快照索引
- `mutations.jsonl`：重要变更日志（append-only，逐行 JSON）
- `retcons.jsonl`：retcon 变更日志（append-only，逐行 JSON）

Schema：
- `status_history.json` -> `../_schema/status_history.schema.json`
- `mutations.jsonl`（单行对象） -> `../_schema/mutation_log_entry.schema.json`
- `retcons.jsonl`（单行对象） -> `../_schema/retcon_log_entry.schema.json`

## 操作指引
1. 所有关键写操作都要写入 `mutations.jsonl`。
2. 发生 retcon 时必须额外写入 `retcons.jsonl`。
3. `status_history.json` 与 `status/history/` 快照保持一一对应。
4. 日志按时间顺序追加，禁止删除历史记录。
