# 5400 s 支撑系统接触运动学修复 RAC 诊断共享包（v20）

本目录是单一 `RAC_5400s` 工况的 GitHub 共享副本，来源于本地 v20 诊断资产。它记录一次 5400 s 运行的输入、源数据、运行结果、分片后的完整大型结果，以及运行后阶段审核。共享副本不修改本地原始资产和原始封印。

## 使用边界

- 本包是单 RAC、5400 s 诊断包，不是 14/18 工况矩阵。
- 运行后阶段审核封印的决定为 `GO_DIAGNOSTIC_ONLY`。
- `paper_evidence_promoted=false`，且多工况矩阵未获授权。
- 土体位移和土体力的工程适用性 gate 均为 `not_evaluated_no_authoritative_project_limit`。
- 用户自行判断本包适合何种后续用途；本目录不替用户作论文适用性、证据晋级或工程容差决定。

上述边界不否定已记录的运行事实：`status.json` 为 `complete`，首次运行、未重试；`gate.json` 为 `pass`。运行保留 54,001 帧、54,000 个接受步和 54,000 个主校正器收敛步，未发生 rescue 或缓冲端止挡帧。求解代码提交为 `1965eabd7cd38a0d441f98c1503491ff8e3465fe`。

## 完整数据与分片

- `result/full_resolution_metrics.csv.gz`：完整分辨率标量时程，25,439,727 bytes，逐字节复制。
- `raw_result_decimated_1s.json.gz`：原始大小 225,683,651 bytes；共享包中无损拆为 5 片。
- `accepted_corrector_trace.ndjson`：原始大小 77,671,919 bytes；共享包中无损拆为 2 片。
- 每片不超过 50,331,648 bytes（48 MiB）。原始大小/SHA-256、分片顺序/大小/SHA-256、PowerShell 与 Python 重组命令均见 `CHUNKS.json`。
- 两个原始大文件未直接纳入共享目录；`__pycache__` 未纳入。

分片按 `CHUNKS.json` 中的 `order` 顺序直接拼接即可无损恢复。恢复后必须同时核对 `original_bytes` 和 `original_sha256`。

## 脱敏和哈希边界

输入、profile JSON、元数据、审核和结果 JSON 中的本机绝对路径已替换为 `source_ref:`、`artifact_ref:`、`repo_ref:` 或 `local_ref:`；所有数值叶节点保持不变。逐文件原始/共享 SHA-256、替换位置和数值不变检查见 `audits/JSON_SANITIZATION_AUDIT.json`。

4 个源 CSV 和完整分辨率标量 gzip 为逐字节复制；profile JSON 因路径脱敏而重新序列化。对应核验见 `audits/SOURCE_COPY_AUDIT.json` 与 `audits/SCALAR_COPY_AUDIT.json`。

本地 `result_seal.json`、`hashes.json` 和审核封印中的哈希保留原运行资产血缘。共享副本的字节级权威为 `PACKAGE_MANIFEST.json`，复核结果见 `PACKAGE_VERIFICATION.json`。为避免循环依赖，manifest 不包含自身和 verification。

## 目录

- `metadata/`：manifest、ready seal、preflight、输入差异与源扩展审计。
- `reviews/`：运行后阶段审核及封印。
- `inputs/`：脱敏后的 `RAC_5400s.json`。
- `source_data/`：4 个源 CSV 和脱敏后的 AQWA profile JSON。
- `result/`：metrics、gate、status、progress、hashes、result seal 和完整分辨率标量时程。本地结果中没有 `module_origin_audit.json`，因此共享包未虚构该文件。
- `chunks/`：两个大型原始结果的无损分片。
- `audits/`：脱敏、源复制和标量复制审计。

机器索引见 `DATA_INDEX.json`；人工索引见 `DATA_INDEX.md`。
