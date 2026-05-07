# `.book` 数据目录（索引）

本项目是单书模式，所有小说数据都在 `.book/`。

## 写作工作流（详细）

默认流程：`Plan -> Draft -> Preflight -> Commit`

### 1. Plan（规划）
目标：明确“这一章要完成什么”，并锁定边界，避免无效写作。

输入来源：
- `outline/`：Arc 与 Chapter 目标、依赖、推进顺序
- `status/current_status.md`：当前全局进度
- `threads/`：必须推进或回收的线程
- `style/voice.md`：文风与叙事约束

建议动作：
- 选择目标 `chapter_id`
- 确认前置章节是否已满足
- 明确本章必达目标（情节推进、角色推进、线程推进）
- 列出本章禁止违反的硬约束（角色设定、世界规则）

输出结果：
- 更新或确认 `outline/chapters/<chapter_id>.md`
- 形成本章写作任务清单（可放在章节文件或 scene card）

### 2. Draft（起草）
目标：生成候选正文与候选事实，但不直接污染 canon。

输入来源：
- Plan 阶段的章节目标
- `characters/`、`relationships/`、`world/`、`timeline/`

建议动作：
- 在 `.book/drafts/` 生成章节草稿
- 记录本章新增事实候选（例如关系变化、世界规则补充、关键事件）
- 标注不确定点，等待预检阶段判断

输出结果：
- `.book/drafts/` 下的草稿文件
- 候选变更列表（角色/关系/世界/时间线）

### 3. Preflight（提交前预检）
目标：在入典前做一致性闸门，发现冲突立即阻断。

检查范围：
- 大纲一致性：是否达成本章目标，是否越级推进
- 角色一致性：动机、能力、关系是否突变
- 世界一致性：是否违反硬规则
- 时间线一致性：事件顺序与因果是否成立
- 线程一致性：该推进/回收的伏笔是否遗漏

判定结果：
- `PASS`：可提交
- `BLOCKED`：发现冲突，必须修复后重检
- `PASS_WITH_RETCON`：仅在显式允许 retcon 时通过，并需记录变更原因

输出结果：
- 预检报告（通过/阻断 + 问题清单 + 最小修复建议）

### 4. Commit（入典）
目标：把通过预检的内容写入正式真相源，并记录审计轨迹。

建议动作顺序：
1. 将草稿写入 `chapters/`
2. 抽取关键事件更新 `timeline/`
3. 如有变更，同步更新 `characters/`、`relationships/`、`world/`
4. 更新 `status/current_status.md`
5. 在 `status/history/` 追加快照
6. 在 `logs/` 追加审计日志

输出结果：
- 正式章节入典
- 全局状态刷新
- 历史与日志可追溯

## 失败与回滚策略

- 若 Preflight 为 `BLOCKED`：禁止 Commit，只允许修复草稿或调整计划。
- 若发现已提交内容有硬冲突：走 retcon 流程，必须在日志中记录原因、影响范围和审批信息。
- 推荐在重大变更前做备份快照，避免连续会话中的误覆盖。

## 每次会话结束前检查

- `current_status.md` 是否反映最新章节结果
- `outline` 是否更新了章节状态
- 线程（`threads/`）是否更新 open/resolved
- 日志是否记录了本次关键变更

## 目录快速索引

详细字段说明请查看各目录内 `README.md`：

- `outline/README.md`
- `characters/README.md`
- `world/README.md`
- `chapters/README.md`
- `timeline/README.md`
- `relationships/README.md`
- `status/README.md`
- `indexes/README.md`
- `logs/README.md`
- `style/README.md`
- `threads/README.md`
- `scene_cards/README.md`
- `drafts/README.md`
- `canon/README.md`
