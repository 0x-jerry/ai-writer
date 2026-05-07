# `outline/` 说明

负责小说结构真相源（Arc -> Chapter）。

- `master_outline.md`：总纲入口（主线、Arc 列表、整体推进）
- `arcs/*.md`：每个 Arc 的冲突、目标、起止范围
- `chapters/*.md`：每章目标、前置依赖、关键角色、必须推进线程

用途：`chapter-preflight` 用此验证章节是否偏离结构目标。

## 操作指引
1. 新增章节前，先在 `chapters/` 建立 `ch-xxx.md` 并写清章节目标。
2. 每个章节必须写 `前置章节`，没有依赖则写空数组。
3. 完成章节后，把章节状态从 `planned` 更新为 `draft_done/finalized`。
4. Arc 状态要与章节推进同步更新，避免 Arc 与章节状态冲突。
