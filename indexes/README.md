# `indexes/` 说明

机器可读索引目录（JSON）。

## `outline_index.json`
职责：维护 Arc/Chapter 索引，支持依赖检查和快速定位。

### Schema（JSON Schema Draft 2020-12）
```json
{
  "$schema": "https://json-schema.org/draft/2020-12/schema",
  "title": "OutlineIndex",
  "type": "object",
  "required": ["arcs", "chapters", "updated_at"],
  "properties": {
    "arcs": {
      "type": "array",
      "items": {
        "type": "object",
        "required": ["arc_id", "title", "status"],
        "properties": {
          "arc_id": { "type": "string", "pattern": "^arc-[a-zA-Z0-9_-]+$" },
          "title": { "type": "string" },
          "status": { "type": "string", "enum": ["planned", "in_progress", "completed", "on_hold"] },
          "start_chapter_id": { "type": ["string", "null"] },
          "end_chapter_id": { "type": ["string", "null"] }
        },
        "additionalProperties": false
      }
    },
    "chapters": {
      "type": "array",
      "items": {
        "type": "object",
        "required": ["chapter_id", "arc_id", "title", "status", "dependencies"],
        "properties": {
          "chapter_id": { "type": "string", "pattern": "^ch-[a-zA-Z0-9_-]+$" },
          "arc_id": { "type": "string", "pattern": "^arc-[a-zA-Z0-9_-]+$" },
          "title": { "type": "string" },
          "status": { "type": "string", "enum": ["planned", "in_progress", "draft_done", "finalized"] },
          "goal": { "type": "string" },
          "dependencies": {
            "type": "array",
            "items": { "type": "string", "pattern": "^ch-[a-zA-Z0-9_-]+$" }
          },
          "key_characters": { "type": "array", "items": { "type": "string" }, "default": [] },
          "required_threads": { "type": "array", "items": { "type": "string" }, "default": [] }
        },
        "additionalProperties": false
      }
    },
    "updated_at": { "type": ["string", "null"], "format": "date-time" }
  },
  "additionalProperties": false
}
```

### 最小示例
```json
{
  "arcs": [],
  "chapters": [],
  "updated_at": null
}
```
