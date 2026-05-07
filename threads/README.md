# `threads/` 说明

伏笔/承诺/谜团追踪目录（open loops）。

建议每个线程单文件，建议字段：
- `thread_id`
- `introduced_in`
- `owner`
- `expected_payoff_by`
- `status`（open/resolved）
- `resolved_in`

用途：确保伏笔可追踪、可回收。

## 操作指引
1. 新增伏笔时立即建线程文件并标注 `introduced_in`。
2. 每章结束检查“必须推进线程”是否已更新。
3. 回收线程后必须填写 `resolved_in`。
4. 禁止无记录地删除线程文件。
