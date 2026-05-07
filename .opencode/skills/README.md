# Novel Skills Pack（单书版）

本目录包含 6 个技能，面向单书小说项目，数据根目录固定为 `.book/`。

## 技能列表
- `outline-keeper`: 大纲守护（Arc -> Chapter）
- `character-weaver`: 角色关系与角色状态
- `world-continuity`: 世界观连续性守护
- `session-status-manager`: 会话状态与历史快照
- `chapter-preflight`: 章节提交前一致性预检
- `canon-committer`: 草稿入典与变更审计

## 全局规则
- 单书项目：禁止多书模型与 `book_id`
- 默认流程：`Plan -> Draft -> Preflight -> Commit`
- 冲突策略：默认阻断，只有显式 `retcon=true` 才允许继续并记录
- 输出格式：`行动清单 + 补丁文本`

## 自动触发建议
- 任务出现「大纲/下一章/章节目标」时触发 `outline-keeper`
- 出现「角色关系/人设/角色上下文」时触发 `character-weaver`
- 出现「设定/规则/地点/势力」时触发 `world-continuity`
- 出现「当前进度/跨会话状态」时触发 `session-status-manager`
- 出现「提交前检查/连续性检查」时触发 `chapter-preflight`
- 出现「入典/定稿/落库/变更记录」时触发 `canon-committer`
