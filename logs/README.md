# `logs/` 说明

审计日志目录（JSON / JSONL）。

## `status_history.json`
职责：状态快照索引，支持快速回溯。

### Schema
```json
{
  "$schema": "https://json-schema.org/draft/2020-12/schema",
  "title": "StatusHistoryIndex",
  "type": "object",
  "required": ["entries"],
  "properties": {
    "entries": {
      "type": "array",
      "items": {
        "type": "object",
        "required": ["ts", "snapshot_file", "chapter_id", "summary"],
        "properties": {
          "ts": { "type": "string", "format": "date-time" },
          "snapshot_file": { "type": "string" },
          "chapter_id": { "type": ["string", "null"], "pattern": "^ch-[a-zA-Z0-9_-]+$" },
          "summary": { "type": "string" }
        },
        "additionalProperties": false
      }
    }
  },
  "additionalProperties": false
}
```

### 最小示例
```json
{
  "entries": []
}
```

## `mutations.jsonl`
职责：重要变更日志（append-only，逐行 JSON）。

### 单行对象 Schema
```json
{
  "$schema": "https://json-schema.org/draft/2020-12/schema",
  "title": "MutationLogEntry",
  "type": "object",
  "required": ["ts", "skill", "action", "targets", "retcon"],
  "properties": {
    "ts": { "type": "string", "format": "date-time" },
    "skill": {
      "type": "string",
      "enum": [
        "outline-keeper",
        "character-weaver",
        "world-continuity",
        "session-status-manager",
        "chapter-preflight",
        "canon-committer"
      ]
    },
    "action": { "type": "string" },
    "chapter_id": { "type": ["string", "null"], "pattern": "^ch-[a-zA-Z0-9_-]+$" },
    "targets": { "type": "array", "items": { "type": "string" }, "minItems": 1 },
    "summary": { "type": "string" },
    "retcon": { "type": "boolean" }
  },
  "additionalProperties": false
}
```

### 示例（单行）
```json
{"ts":"2026-05-07T09:00:00Z","skill":"canon-committer","action":"commit_chapter","chapter_id":"ch-001","targets":[".book/chapters/ch-001.md",".book/timeline/ch-001.md"],"summary":"提交第一章并更新时间线","retcon":false}
```

## `retcons.jsonl`
职责：retcon 变更日志（append-only，逐行 JSON）。

### 单行对象 Schema
```json
{
  "$schema": "https://json-schema.org/draft/2020-12/schema",
  "title": "RetconLogEntry",
  "type": "object",
  "required": ["ts", "chapter_id", "reason", "impacted_entities", "approved_by"],
  "properties": {
    "ts": { "type": "string", "format": "date-time" },
    "chapter_id": { "type": ["string", "null"], "pattern": "^ch-[a-zA-Z0-9_-]+$" },
    "reason": { "type": "string" },
    "impacted_entities": { "type": "array", "items": { "type": "string" }, "minItems": 1 },
    "changes": { "type": "array", "items": { "type": "string" }, "default": [] },
    "approved_by": { "type": "string" }
  },
  "additionalProperties": false
}
```

### 示例（单行）
```json
{"ts":"2026-05-07T10:30:00Z","chapter_id":"ch-003","reason":"修复时间线硬冲突","impacted_entities":["character:lin","timeline:event-22"],"changes":["角色到达时间后移两天"],"approved_by":"author"}
```

## 维护约束
- `*.jsonl` 必须 append-only
- 时间统一 ISO 8601 UTC（如 `2026-05-07T10:30:00Z`）
