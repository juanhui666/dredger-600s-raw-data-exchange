# 数据索引

## 工况顺序

1. `RAC`
2. `R0`
3. `RA`
4. `RC`
5. `B_P85_N9`
6. `B_P185_N9`
7. `S_L35_M200`
8. `S_L35_M325`
9. `S_L35_M450`
10. `S_L40_M200`
11. `S_L40_M450`
12. `S_L45_M200`
13. `S_L45_M325`
14. `S_L45_M450`
15. `S_L375_M325`
16. `S_L425_M325`
17. `S_L40_M2625`
18. `S_L40_M3875`

每个 `cases/<case_id>/` 均包含：

- `metrics.json`：运行统计与响应摘要；
- `gate.json`：工况 gate 结果；
- `status.json`：执行状态；
- `module_origin_audit.json`：运行模块来源审计；
- `result_seal.json`：本地原运行结果的血缘封印副本；
- `full_resolution_metrics.csv.gz`：完整分辨率标量时程。

对应输入位于 `inputs/<case_id>.json`。

## 外部源数据

- `source_data/aqwa_bridge_0_600s.csv`
- `source_data/aqwa_hull_0_600s.csv`
- `source_data/aqwa_spud_0_600s.csv`
- `source_data/cutter_constant_mean_0_600s.csv`
- `source_data/cutter_projected_0_600s.csv`

## 元数据、审核和分析

- `metadata/` 包含 `case_matrix.json`、`manifest.json`、`input_diff_audit.json`、`source_and_import_audit.json`、`pre_run_report.json`、`ready_candidate_seal.json`、`review_contracts.json`。
- `reviews/` 包含全部阶段审核、候选审核和审核封印，具体清单见 `DATA_INDEX.json`。
- `matrix_analysis/matrix_analysis.json` 是机器可读矩阵分析；`matrix_analysis/interaction_and_pressure_curvature_steady.csv.gz` 是派生表；`matrix_analysis/result_seal.json` 是分析资产封印副本。
- `audits/` 记录输入/JSON 脱敏、源 CSV 逐字节复制，以及未纳入大文件的逐工况哈希。

## 完整性入口

- `PACKAGE_MANIFEST.json`：共享包文件大小与 SHA-256 清单。
- `PACKAGE_VERIFICATION.json`：清单复核、JSON 解析、UTF-8、绝对路径扫描、工况与源文件计数结果。

原运行封印用于血缘追踪；共享副本的字节完整性以 `PACKAGE_MANIFEST.json` 为准。
