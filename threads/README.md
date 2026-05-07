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
