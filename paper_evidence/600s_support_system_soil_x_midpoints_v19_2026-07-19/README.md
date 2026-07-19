# 600 s 支撑系统工况数据（桩土 X 位移审计与中点补充）

> **历史数据提示：**本目录使用修复前不完整的桩土 X 运动映射，只保留作运行记录，不再作为桩土接触点响应的物理证据。修复后的单一 RAC 工况见 [`paper_evidence/600s_support_system_contact_kinematics_repair_rac_v19_2026-07-19/`](../600s_support_system_contact_kinematics_repair_rac_v19_2026-07-19/)。

本目录只整理工况、计算状态、响应字段和证据边界，不提供论文结论、参数推荐或章节观点。

## 数据范围

- `v18`：14 个工况，每案计算 600 s，时间步长 0.1 s，共 6001 帧和 6000 个固定 Newmark 步。
- `v19`：在 `v18` 范围内增加 4 个中点工况，每案计算 600 s，时间步长 0.1 s，共 6001 帧和 6000 个固定 Newmark 步。
- 两批共 18 个计算工况，全部状态为 `complete`，全部使用主校正器完成，`rescue`、`reject` 和 `nonconvergence` 计数均为 0。
- 全部工况启用横摇自由度。

## 工况变量

- 载荷组合：无/有 AQWA 环境载荷与恒定均值/波动绞刀载荷的四种组合。
- 缓冲系统：每支路蓄能器数固定为 9，平均初始压力为 85、135 或 185 bar。
- 定位桩入土深度：3.5、3.75、4.0、4.25、4.5 m。
- 土体水平抗力系数：2.00、2.625、3.25、3.875、4.50 MN/m^4。
- 中点工况仅沿一个参数轴变化：固定土体水平抗力系数 3.25 MN/m^4 改变入土深度，或固定入土深度 4.0 m 改变土体水平抗力系数。

## 文件说明

1. `case_inventory.csv`：18 个工况的载荷组合、缓冲参数、桩土参数和完成状态。
2. `response_summary_18case.csv`：18 个工况统一口径的原始响应统计量；未计算相对变化率或推荐值。
3. `soil_x_audit_summary.csv`：定位桩相对固定土体参考的纵向位移审计结果。
4. `midpoint_axis_summary.csv`：深度轴和土体水平抗力系数轴的 10 个取值点，不含趋势判定。
5. `run_records/`：两批运行的矩阵、输入审计、运行封印和证据状态。
6. `case_records/`：逐工况 `metrics.json`、`analysis.json`、`soil_x_audit.json`、状态、哈希及 gate 记录。

## 字段口径

- 桩土 X 位移是定位桩相对固定土体参考的纵向位移，不是定位桩相对缓冲台车的位移。
- `source_only` 表示缓冲行程范围内的模型响应；`proxy_only` 表示达到行程边界后的刚性止挡续算代理。
- 刚性止挡续算结果不代表真实液压冲击、结构强度或安全性。
- 支撑总量含预载；`runtime_delta` 字段是运行时增量口径。
- 桥架铰接点纯力矩为模型规定的零值。

## 证据状态

两批运行封印均记录为 `diagnostic_complete_non_promotable_without_independent_stage_review`，且 `report_use.allowed=false`。因此，这些文件可用于独立审核和后续章节筹划，未经独立阶段审核不得写成普适规律、因果结论、最优参数、安全结论或设计级建议。

本目录未上传每案约 246 MB 的 `raw_result.json.gz` 和约 8.6 MB 的校正器逐步轨迹；这些大文件保存在本地封印运行包中，逐案哈希记录已随 `case_records/` 和运行封印提供。

GitHub 中的 JSON 和 Markdown 为便于浏览统一使用 LF 换行；运行封印和逐案 `hashes.json` 内的哈希仍指向本地封印包的原始文件字节。GitHub 共享副本自身的文件哈希以 `PACKAGE_MANIFEST.json` 为准。
