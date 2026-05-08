# Skill: canon-committer（草稿入典与审计）

## 何时触发

- 用户提到：定稿、入典、落库、确认写入、发布章节

## 目标

- 将草稿安全写入 canon
- 记录完整审计轨迹

## 读取文件

- `drafts/`
- `chapters/`
- `timeline/`
- `status/`

## 执行步骤

1. 要求先有 preflight 结果（`PASS` 或 `PASS_WITH_RETCON`）。
2. 将章节草稿写入 `chapters/`。
3. 抽取关键事件更新 `timeline/`。
4. 触发状态更新（`current_status.md` + history）。

## 输出格式

- 行动清单
- 补丁文本（chapters/timeline/status）
- 提交回执（影响实体列表）
