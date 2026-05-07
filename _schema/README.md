# `_schema/` 说明

JSON Schema 目录，定义本项目 JSON/JSONL 的数据结构约束。

当前 schema：
- `outline_index.schema.json`
- `status_history.schema.json`
- `mutation_log_entry.schema.json`（对应 `logs/mutations.jsonl` 的单行对象）
- `retcon_log_entry.schema.json`（对应 `logs/retcons.jsonl` 的单行对象）

## 操作指引
1. 修改 JSON 结构前先修改对应 schema。
2. 所有 JSON 文件必须设置正确的 `$schema` 相对路径。
3. JSONL 使用“单行对象 schema”，更新后要同步更新日志写入逻辑。
4. schema 更新后，回查受影响文件是否仍兼容。
