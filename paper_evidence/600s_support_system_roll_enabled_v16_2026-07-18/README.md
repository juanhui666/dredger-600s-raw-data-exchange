# 600 s 支撑系统 14 工况数据包（横摇自由度启用版）

本目录仅整理横摇自由度启用后的 14 个计算工况、响应字段和运行状态，不提供论文提纲、写作任务或推荐结论。

此前的横摇锁定结果不属于本目录。使用者应以本目录中的 `run_matrix.json`、`matrix_summary.json` 和运行封印识别本批工况。

## 文件说明

1. `run_matrix.json`：14 个工况的变量、参数值和分组定义。
2. `case_summary.csv`：逐工况响应字段汇总。
3. `relative_to_RAC.csv`：各工况相对 RAC 基准的逐字段数值变化。
4. `soil_3x3_descriptive.csv`：入土深度与土体水平抗力系数 3×3 工况的逐字段数据。
5. `matrix_summary.json`：机器可读的完整汇总。
6. `manifest.json`、`run_manifest.json`、`source_results_integrity.json`：来源和完整性记录。
7. `post_run_result_seal.json`、`post_review_seal.json`、`ready_seal.json`：运行与审核状态记录。

## 工况与计算状态

- 14/14 个工况均完成 600 s 计算，每案 6001 帧、6000 个固定 Newmark 步。
- 全部 84000 个时间步均由主校正器收敛，rescue、reject、nonconvergence 均为 0。
- 横摇自由度在全部工况和全部帧中均为 `free_dynamic`，角度和角速度单位分别为 deg、deg/s。
- 载荷组合为 R0、RA、RC、RAC；内部代号仅用于工况表、图例和方法说明。
- 缓冲系统变量为蓄能器初始压力 85、135、185 bar，每支路蓄能器数固定 N=9。
- 定位桩实际入土深度 L=3.5、4.0、4.5 m；土体水平抗力系数 m=2.00、3.25、4.50 MN/m^4。

## 字段与模型状态

- 每个工况为一次数值计算，没有重复样本或统计试验组。
- 行程到限后的状态使用刚性止挡低频续算代理；相关域标记保存在汇总字段中。
- 桥架铰接点纯力矩为模型规定的零值。
- 支撑总量字段包含预载；工况差值字段采用运行时增量口径。
- 横摇角和角速度单位分别为 deg 和 deg/s，其自由度状态为 `free_dynamic`。

本包不含原始 600 s 压缩时程、求解器代码、论文正文和内部运行目录。
