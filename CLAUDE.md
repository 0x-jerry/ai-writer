# 数据目录（索引）

本项目是单书模式，所有小说数据都在仓库根目录的固定文件夹中。

## 重要提示

在写入任何文件之前，一定要先仔细阅读对应文件夹的 README 文件。

## 写作提示

- 每次场景之间的转换都需要先过渡一下。
- 每章开始的时候也需要先过渡一下。

## 写作工作流（详细）

默认流程：`Plan -> Draft -> Preflight -> Commit`

**禁止自动进入下一个流程，所有流程转换必须先询问用户，同意之后才能执行。**

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

- 在 `drafts/` 生成章节草稿
- 记录本章新增事实候选（例如关系变化、世界规则补充、关键事件）
- 标注不确定点，等待预检阶段判断

输出结果：

- `drafts/` 下的草稿文件
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
- `style/README.md`
- `threads/README.md`
- `scene_cards/README.md`
- `drafts/README.md`
- `canon/README.md`

## 术语表

### 流程术语

- `Plan`：规划阶段，定义目标章节、约束、依赖与必须推进项。
- `Draft`：起草阶段，在 `drafts/` 生成候选正文和候选事实。
- `Preflight`：提交前一致性检查阶段，决定是否允许入典。
- `Commit`：入典阶段，将通过检查的内容写入正式目录并记录日志。

### 判定术语

- `PASS`：通过预检，可执行 commit。
- `BLOCKED`：预检失败，禁止 commit，必须先修复。
- `PASS_WITH_RETCON`：允许提交，但属于设定修订流程，必须记 retcon 日志。
- `retcon`：对既有 canon 的追认修订（通常用于修复硬冲突）。

### 结构术语

- `Arc`：剧情弧（一个中期叙事阶段），由多个章节组成。
- `Chapter`：章节，最小提交单元。
- `Scene`：场景，章节内部的推进单元。
- `outline`：结构真相源，定义 Arc/Chapter 的目标与依赖。
- `canon`：已确认的正式内容（正文与结构化事实）。

### ID 与状态术语

- `arc_id`：Arc 唯一标识，建议形如 `arc-001`。
- `chapter_id`：Chapter 唯一标识，建议形如 `ch-001`。
- 章节状态：`planned`（已规划）、`in_progress`（写作中）、`draft_done`（草稿完成）、`finalized`（已入典）。
- Arc 状态：`planned`、`in_progress`、`completed`、`on_hold`。

### 连续性术语

- `dependency`：章节依赖，表示某章节必须在本章之前完成。
- `key_characters`：本章必须重点推进的角色集合。
- `required_threads`：本章必须推进/回收的线程集合。
- `thread`：伏笔/承诺/谜团的追踪单元。
- `open thread`：尚未回收的线程。
- `resolved thread`：已回收并闭环的线程。

### 角色与世界术语

- 角色一致性：角色动机、能力、关系、行为轨迹不发生无依据突变。
- 世界一致性：世界规则、地点、势力逻辑不被新内容破坏。
- 时间线一致性：事件先后和因果链条可成立。

### 状态与日志术语

- `current_status.md`：唯一实时全局状态文件。
- `status/history/`：状态历史快照目录。

### 技能术语

- `outline-keeper`：维护大纲结构与章节依赖。
- `character-weaver`：维护角色档案、角色关系与角色上下文。
- `world-continuity`：维护世界规则并检查设定冲突。
- `session-status-manager`：维护当前状态与历史快照。
- `chapter-preflight`：执行提交前一致性闸门。
- `canon-committer`：将通过预检内容入典并写审计日志。
