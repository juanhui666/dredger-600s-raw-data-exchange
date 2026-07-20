# 数据索引

## 工况与输入

- 工况：`RAC_5400s`
- 时长：5400 s
- 脱敏输入：`inputs/RAC_5400s.json`

## 源数据

- `source_data/aqwa_bridge_0_5400s.csv`
- `source_data/aqwa_hull_0_5400s.csv`
- `source_data/aqwa_spud_0_5400s.csv`
- `source_data/cutter_projected_periodic_0_5400s.csv`
- `source_data/aqwa_env_body_load_profile_source.json`

前 4 个文件为逐字节复制；profile JSON 已脱敏本机路径。

## 运行结果

- `result/full_resolution_metrics.csv.gz`
- `result/metrics.json`
- `result/gate.json`
- `result/status.json`
- `result/progress.json`
- `result/hashes.json`
- `result/result_seal.json`

源结果目录没有 `module_origin_audit.json`，共享包未生成替代文件。

## 大型结果分片

- `chunks/raw_result_decimated_1s/`：`raw_result_decimated_1s.json.gz` 的 5 个有序分片。
- `chunks/accepted_corrector_trace/`：`accepted_corrector_trace.ndjson` 的 2 个有序分片。
- `CHUNKS.json`：原始文件与各分片的大小、SHA-256、顺序、重组命令和重组验证要求。

## 元数据与审核

- `metadata/manifest.json`
- `metadata/ready_seal.json`
- `metadata/preflight_report.json`
- `metadata/input_diff_audit.json`
- `metadata/source_extension_audit.json`
- `metadata/parent_source_extension_audit_v3.json`
- `reviews/post_run_stage_review.json`
- `reviews/post_run_stage_review_seal.json`

## 完整性入口

- `audits/JSON_SANITIZATION_AUDIT.json`
- `audits/SOURCE_COPY_AUDIT.json`
- `audits/SCALAR_COPY_AUDIT.json`
- `PACKAGE_MANIFEST.json`
- `PACKAGE_VERIFICATION.json`

原运行封印记录本地资产血缘；共享文件字节完整性以 `PACKAGE_MANIFEST.json` 为准。
