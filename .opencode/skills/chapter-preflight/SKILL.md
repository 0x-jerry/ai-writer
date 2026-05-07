# Skill: chapter-preflight（章节预检）

## 何时触发
- 用户提到：提交前检查、一致性检查、能否入典、连续性验证

## 目标
- 在 Commit 前阻断连续性问题
- 输出最小修复建议

## 读取文件
- `outline/`
- `characters/`
- `world/`
- `timeline/`
- `threads/`
- `drafts/` 或待提交草稿

## 检查清单
1. 大纲一致性：是否达成章节目标、是否越级推进。
2. 角色一致性：行为/能力/情绪是否突变。
3. 世界规则一致性：是否违反硬约束。
4. 时间线一致性：事件顺序与因果是否可成立。
5. 线程一致性：是否遗忘必须回收的伏笔。

## 决策规则
- 发现冲突且 `retcon=false`：返回 `BLOCKED`
- `retcon=true`：返回 `PASS_WITH_RETCON` 并要求记录 retcon

## 输出格式
- 结论：`PASS | BLOCKED | PASS_WITH_RETCON`
- 行动清单
- 补丁文本（修复建议）
