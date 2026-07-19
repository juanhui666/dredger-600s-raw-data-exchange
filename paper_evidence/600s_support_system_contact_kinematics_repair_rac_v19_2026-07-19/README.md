# 修复后桩土接触点运动学：RAC 工况 600 s 数据

本目录只共享计算输入、运行状态、工程响应、逐步收敛记录和结果封印，不提供论文观点、参数推荐或章节结论。

## 工况与运行状态

- 工况：RAC，即启用 AQWA 外部环境载荷时程，并采用波动绞刀冲击载荷时程。
- 计算时长 600 s，固定时间步长 0.1 s，共 6001 帧和 6000 个 Newmark 步。
- 6000/6000 步均由主校正器收敛完成，未使用救援求解；最大校正残差为 `9.999281054082904e-7`。
- 本目录只包含修复后的一个 RAC 工况，不代表 14 个工况均已按新模型重算。

## 桩土 X 位移口径

桩土 X 位移定义为定位桩下部土接触材料点相对固定初始参考位置的全局 X 向位移。计算先组合船体平移、船体转动和定位桩相对上铰点转动，再取接触点当前全局 X 坐标与参考坐标之差；不是把船体纵荡直接当作桩土位移，也不是脱离方向和力臂简单相加两个标量。

桩土反力作用于同一接触材料点，并按接触点雅可比通过虚功映射为各广义坐标载荷。共享结果中的位移分解、字段别名和功率映射已通过几何符号、速度一致性及闭合测试。

## 主要原始统计量

以下数值直接来自 `result_RAC/metrics.json`：

- 船体纵荡范围：`-0.4078544269`～`0.1958704208 m`；
- 桩土接触点 X 位移范围：`-0.0126795932`～`0.0301072515 m`；
- 桩土接触点 X 位移与船体纵荡之差的绝对峰值：`0.4375962766 m`；
- 桩土转角绝对峰值：`0.8419275080°`；
- 船体—定位桩相对纵摇角绝对峰值：`2.0754880130°`；
- 两支路液压缸位移绝对峰值：`0.5960393466 m`、`0.6078819950 m`；
- 居中半行程限值：`0.75 m`，达到行程边界的帧数为 `0`；
- 桩土 X 向反力绝对峰值：`545559.8432 N`；
- 定位桩上铰点 O 的 X 向约束反力绝对峰值：`524471.7755 N`。

## 文件说明

1. `input_RAC_shared.json`：本工况完整共享输入；仅将本地绝对路径替换为 `source_ref:` 标识，数值参数未改。
2. `result_RAC/metrics.json`：600 s 原始统计量。
3. `result_RAC/gate.json`、`result_RAC/status.json`：运行 gate 和完成状态。
4. `result_RAC/accepted_corrector_trace.ndjson`：6000 个接受步的校正器逐步记录。
5. `raw_result_chunks/`：`raw_result.json.gz` 的无损分片；分片顺序、大小和哈希见 `RAW_RESULT_CHUNKS.json`。
6. `post_run_result_seal.json`：本地封印原始结果文件的 SHA-256。
7. `post_run_engineering_review_shared.json`：指令出发点、运行过程和结果合理性三段式审核记录；仅替换本地路径。
8. `PACKAGE_MANIFEST.json`：GitHub 共享副本自身的大小和 SHA-256。
9. `PACKAGE_VERIFICATION.json`：对原始运行封印与共享包完整性的复核记录。

## 原始结果重组

PowerShell：

```powershell
$parts = Get-ChildItem raw_result_chunks/raw_result.json.gz.part* | Sort-Object Name
$output = [System.IO.File]::Create('raw_result.json.gz')
try {
  foreach ($part in $parts) {
    $input = [System.IO.File]::OpenRead($part.FullName)
    try { $input.CopyTo($output) } finally { $input.Dispose() }
  }
} finally { $output.Dispose() }
Get-FileHash raw_result.json.gz -Algorithm SHA256
```

重组文件的 SHA-256 应为 `0d2577b488a7fc74faf806105748429a323c845449bffae6a2e70364cc630ed1`。

## 证据边界

- 本次结果只支持核查该 RAC 工况在修复模型下的 600 s 数值响应。
- 原 v18 的 14 工况和原 1.5 h 工况使用不完整的桩土 X 运动映射，保留为历史记录，不作为修复模型的物理证据。
- 当前没有现场标定、设计限值或重复样本；不得据此给出实船验证、普适因果、参数最优、安全裕度或设计级结论。
- 行程内响应可供工程审查，但该单一工况尚未晋级为论文定量结论，也未授权扩展 14 工况矩阵。
- 输入中的内部环境发生器为关闭状态；本工况的环境作用来自已启用的 AQWA 外部载荷时程，因此不得把 `env.wave_height=0` 解释成无环境载荷。

完整性复核中，原 `ready_seal.json` 及 `post_run_result_seal.json` 均与其所列原始文件匹配；原 `post_run_engineering_review_seal.json` 中的审核文件 SHA-256 有 1 个十六进制字符与实测值不符。原封印保留不改，不能用该字段验证审核文件；共享审核副本改由 `PACKAGE_MANIFEST.json` 的 SHA-256 验证。详情见 `PACKAGE_VERIFICATION.json`。

本目录 Markdown 和 JSON 使用 LF 换行。原始运行封印中的哈希指向本地封印字节；GitHub 共享副本的哈希以 `PACKAGE_MANIFEST.json` 为准。
