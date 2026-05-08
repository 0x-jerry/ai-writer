# 共享规范（所有技能必须遵守）

## 标准输入

- `chapter_id`（可选，但章节相关任务必须提供）
- `task_goal`（当前会话目标）
- `involved_characters`（可选）
- `draft_excerpt`（可选）
- `retcon`（默认 `false`）

## 标准输出

1. 行动清单（最多 8 条）
2. 补丁文本（按文件分段，直接可应用）
3. 风险与阻断项

## 一致性规则

- 如果发现与大纲/时间线/角色状态/世界规则冲突：
  - 当 `retcon=false`：必须阻断并返回修复建议
  - 当 `retcon=true`：允许继续，但必须写入 `retcons` 日志

## 变更记录

- 重要变更建议在 `timeline/overview.md` 中记录摘要
