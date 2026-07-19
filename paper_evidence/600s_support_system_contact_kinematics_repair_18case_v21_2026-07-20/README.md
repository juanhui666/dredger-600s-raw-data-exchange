# 600 s 支撑系统接触运动学修复 18 工况共享数据包（v21）

本目录是面向 GitHub 交换的脱敏副本，来源于本地 v21 运行资产。它保存 18 个工况的输入、外部源 CSV、运行摘要、完整分辨率标量时程、矩阵分析结果，以及各阶段审核与封印。共享副本不改写本地原始资产或原始封印。

## 数据边界

- 求解代码提交：`1965eabd7cd38a0d441f98c1503491ff8e3465fe`。
- 工况数：18；正式顺序见 `DATA_INDEX.md` 和 `metadata/case_matrix.json`。
- 每个工况的共享状态为运行完成且 gate 通过；统计窗口由原资产声明为全程 0–600 s、稳态 60–600 s。
- 每个工况保留 `full_resolution_metrics.csv.gz`，18 个文件合计 50,238,974 bytes（约 47.91 MiB）。
- `raw_result_decimated_1s.json.gz` 未纳入，18 个文件合计 451,571,106 bytes（约 430.65 MiB）。
- `accepted_corrector_trace.ndjson` 未纳入，18 个文件合计 155,211,279 bytes（约 148.02 MiB）。
- 被排除文件的逐工况大小与 SHA-256 见 `audits/EXCLUSION_INVENTORY.json`。

本包只陈述运行、审核、文件和数值记录等工程事实。它不新增学术结论，不代表论文证据晋级，也不提供现场标定或工程容差判定。

## 脱敏与可核验性

18 份输入中的本机 CSV 绝对路径已替换为 `source_ref:source_data/<file>`；其他本机资产/仓库路径替换为 `artifact_ref:`、`repo_ref:` 或 `local_ref:`。数值字段保持不变。逐文件原始 SHA-256、共享 SHA-256、替换位置和数值不变检查见 `audits/INPUT_SANITIZATION_AUDIT.json` 与 `audits/JSON_SANITIZATION_AUDIT.json`。

5 个源 CSV 为逐字节复制，原始和共享 SHA-256 相同，见 `audits/SOURCE_COPY_AUDIT.json`。脱敏 JSON 的字节哈希必然可能不同于本地原件；本地 `result_seal.json` 中的哈希用于记录原运行资产血缘，不应当作共享副本字节哈希。共享目录的字节级权威是 `PACKAGE_MANIFEST.json`，复核结果在 `PACKAGE_VERIFICATION.json`。

为避免循环依赖，`PACKAGE_MANIFEST.json` 不列入自身、`PACKAGE_VERIFICATION.json` 和仅用于本地组包且最终删除的临时脚本；README 与两个 DATA_INDEX 均列入清单。

## 目录

- `metadata/`：工况矩阵、manifest、输入差异、源与导入审计、预运行报告、候选封印和审核合同。
- `reviews/`：阶段、RAC 复现、代表批次、全矩阵、矩阵分析的审核记录与封印。
- `inputs/`：18 份脱敏输入 JSON。
- `source_data/`：5 个原始外部源 CSV。
- `cases/<case_id>/`：工况 metrics、gate、status、模块来源审计、原结果封印副本和完整分辨率标量时程。
- `matrix_analysis/`：矩阵分析 JSON、派生 CSV.gz 和分析结果封印。
- `audits/`：脱敏、源复制和排除清单。

机器可读索引见 `DATA_INDEX.json`；人工索引见 `DATA_INDEX.md`。
