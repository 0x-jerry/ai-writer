# `indexes/` 说明

机器可读索引目录（JSON）。

## `outline_index.json`
职责：维护 Arc/Chapter 索引，支持依赖检查和快速定位。

Schema：`../_schema/outline_index.schema.json`

## 操作指引
1. `outline/` 有结构更新时，同步刷新 `outline_index.json`。
2. `chapter_id` 与 `arc_id` 命名必须符合 schema 约束。
3. 写入前校验 JSON 格式与 `$schema` 路径。
4. 索引只记录结构化摘要，不复制正文内容。
