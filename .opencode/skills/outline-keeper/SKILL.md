# Skill: outline-keeper（大纲守护）

## 何时触发
- 用户提到：大纲、Arc、章节规划、下一章写什么、章节依赖

## 目标
- 维护 `outline/` 的 Arc -> Chapter 结构
- 保障章节目标与依赖可追踪

## 读取文件
- `outline/master_outline.md`
- `outline/arcs/`
- `outline/chapters/`
- `indexes/outline_index.json`

## 执行步骤
1. 校验目标 Arc/Chapter 是否存在，若不存在生成最小模板。
2. 更新章节目标、前置依赖、完成状态。
3. 同步更新 `outline_index.json`。
4. 返回下一章候选及原因（基于未完成且依赖满足）。

## 输出格式
- 行动清单
- 补丁文本（涉及 `master_outline.md`、arc/chapter 文件、`outline_index.json`）
- 风险说明（依赖缺失/重复目标/冲突）

## 模板（章节节点）
```md
# Chapter: <chapter_id>

- 所属 Arc: <arc_id>
- 状态: planned | in_progress | draft_done | finalized
- 章节目标: <goal>
- 前置章节: [<chapter_id>, ...]
- 关键角色: [<name>, ...]
- 必须推进的线程: [<thread_id>, ...]
```
