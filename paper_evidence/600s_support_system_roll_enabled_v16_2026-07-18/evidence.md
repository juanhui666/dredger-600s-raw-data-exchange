# 14-case roll-enabled pattern evidence v16

Status: derived evidence only; not a paper or manuscript section.

All 14 source cases are complete, gate PASS, and their six declared result-file hashes were recomputed and matched before derivation.

## Evidence boundaries

- Wording is limited to candidate patterns and observations; no causal or inferential extrapolation is authorized.
- source_only is the source-paper within-stroke domain. proxy_only is an ideal low-frequency post-stroke continuation domain, not impact or safety evidence.
- Roll is enabled and reports free_dynamic provenance in every case and every frame; roll angle and rate outputs are in degrees and degrees per second.
- The parent v13/v14 results remain preserved but are superseded for the current manuscript because their roll DOF was disabled.
- The hinge reaction moment is a model-imposed zero: the hinge transmits force but no pure moment.
- Support total_physical_dynamic_balance includes preload. Pattern metrics use explicit dynamic_balance_runtime_delta fields.
- Cumulative soil energy is not filtered by frame domain. Source/proxy/transition contributions sum trapezoidal interval increments.
- report_use is limited to descriptive computational claims within these 14 cases and the source_only model domain; no causal, optimal, safety, or design-grade claim is allowed.

## Per-case domain and energy evidence

| Case | Groups | Source frames (%) | Proxy frames (%) | Roll RMS/peak (deg) | B1 end/slack | B2 end/slack | First/last end stop (s) | Soil energy total (J) | Source/proxy/transition contribution (J) |
|---|---|---:|---:|---:|---:|---:|---:|---:|---:|
| RAC | load_decomposition, buffer_pressure, soil_3x3 | 5830 (97.15) | 171 (2.85) | 0.161/0.63 | 92/0 | 171/3 | 40.2/595 | 9.7549e+06 | 7.8574e+06/8.1075e+05/1.0868e+06 |
| R0 | load_decomposition | 6001 (100.00) | 0 (0.00) | 0.122/0.122 | 0/0 | 0/0 | NA/NA | 6.7829e-12 | 6.7829e-12/0/0 |
| RA | load_decomposition | 5836 (97.25) | 165 (2.75) | 0.164/0.626 | 90/0 | 165/4 | 45.6/595 | 9.7293e+06 | 7.8061e+06/8.1814e+05/1.1051e+06 |
| RC | load_decomposition | 6001 (100.00) | 0 (0.00) | 0.124/0.143 | 0/0 | 0/0 | NA/NA | 3103.2 | 3103.2/0/0 |
| B_P85_N9 | buffer_pressure | 5601 (93.33) | 400 (6.67) | 0.193/0.738 | 289/1 | 400/166 | 39.9/599 | 1.9263e+07 | 1.2907e+07/2.8341e+06/3.5222e+06 |
| B_P185_N9 | buffer_pressure | 5981 (99.67) | 20 (0.33) | 0.157/0.609 | 3/0 | 20/0 | 65.1/396 | 5.1721e+06 | 5.0855e+06/42735/43859 |
| S_L35_M200 | soil_3x3 | 5782 (96.35) | 219 (3.65) | 0.183/0.58 | 157/6 | 219/37 | 52.9/575 | 2.8498e+07 | 2.4347e+07/1.5961e+06/2.555e+06 |
| S_L35_M325 | soil_3x3 | 5884 (98.05) | 117 (1.95) | 0.171/0.597 | 71/0 | 117/3 | 45.8/596 | 1.1573e+07 | 1.0124e+07/5.8691e+05/8.6234e+05 |
| S_L35_M450 | soil_3x3 | 5903 (98.37) | 98 (1.63) | 0.167/0.637 | 37/0 | 98/1 | 39.6/588 | 7.0984e+06 | 6.3088e+06/3.7715e+05/4.1245e+05 |
| S_L40_M200 | soil_3x3 | 5730 (95.48) | 271 (4.52) | 0.196/0.576 | 193/3 | 271/35 | 46.1/574 | 2.3088e+07 | 1.8585e+07/1.8634e+06/2.6404e+06 |
| S_L40_M450 | soil_3x3 | 5879 (97.97) | 122 (2.03) | 0.164/0.683 | 64/0 | 122/2 | 39.5/588 | 6.8712e+06 | 5.5417e+06/6.0701e+05/7.2249e+05 |
| S_L45_M200 | soil_3x3 | 5683 (94.70) | 318 (5.30) | 0.206/0.609 | 200/0 | 318/37 | 40.1/596 | 2.1303e+07 | 1.6365e+07/2.2151e+06/2.7234e+06 |
| S_L45_M325 | soil_3x3 | 5786 (96.42) | 215 (3.58) | 0.16/0.681 | 115/0 | 215/4 | 39.9/595 | 8.9341e+06 | 6.7149e+06/1.1013e+06/1.1179e+06 |
| S_L45_M450 | soil_3x3 | 5835 (97.23) | 166 (2.77) | 0.17/0.673 | 76/0 | 166/3 | 39.4/589 | 6.4103e+06 | 4.7635e+06/8.3835e+05/8.0846e+05 |

## Candidate group observations relative to RAC

Percent change is (case-RAC)/abs(RAC)*100; NA means the RAC denominator is zero or unavailable.

### load_decomposition

| Case | Energy total | Roll RMS | Buffer pitch RMS | B1 stroke p95 | Soil x RMS | Soil moment abs peak | Support delta Fx RMS | Support delta pitch RMS |
|---|---:|---:|---:|---:|---:|---:|---:|---:|
| R0 | -100 | -24 | -49.8 | -72.5 | -100 | -82.9 | -100 | -99.2 |
| RA | -0.263 | 2.08 | 0.00521 | 0.207 | -0.0731 | 2.05 | -0.239 | -0.0407 |
| RC | -100 | -23.1 | -50.3 | -72.2 | -99.2 | -82.7 | -97.4 | -98.9 |
| RAC | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |

### buffer_pressure

| Case | Energy total | Roll RMS | Buffer pitch RMS | B1 stroke p95 | Soil x RMS | Soil moment abs peak | Support delta Fx RMS | Support delta pitch RMS |
|---|---:|---:|---:|---:|---:|---:|---:|---:|
| B_P85_N9 | 97.5 | 20.3 | 15.4 | 3.1 | 16.1 | 2.29 | 10.6 | -1.74 |
| RAC | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| B_P185_N9 | -47 | -2.11 | -19.5 | -15.3 | -21.8 | -23.9 | -2.34 | 0.848 |

## Soil 3x3 descriptive candidate patterns

Classifications describe only this computed 3x3 grid. Interaction is descriptive effect variation and a corner difference-in-differences, without causal interpretation.

| Metric | Fixed L, vary m classifications | Fixed m, vary L classifications | Corner difference-in-differences |
|---|---|---|---:|
| soil_energy_total_J | L=3.5:nonincreasing, L=4.0:nonincreasing, L=4.5:nonincreasing | m=2.0:nonincreasing, m=3.25:nonincreasing, m=4.5:nonincreasing | 6.5063e+06 |
| roll_phi_rms_deg | L=3.5:nonincreasing, L=4.0:nonmonotonic, L=4.5:nonmonotonic | m=2.0:nondecreasing, m=3.25:nonincreasing, m=4.5:nonmonotonic | -0.020787 |
| buffer_relative_pitch_rms_rad | L=3.5:nonincreasing, L=4.0:nonincreasing, L=4.5:nonincreasing | m=2.0:nondecreasing, m=3.25:nondecreasing, m=4.5:nondecreasing | -0.0010505 |
| branch1_stroke_utilization_p95 | L=3.5:nonincreasing, L=4.0:nonmonotonic, L=4.5:nonincreasing | m=2.0:nondecreasing, m=3.25:nondecreasing, m=4.5:nondecreasing | 0.016727 |
| soil_x_displacement_rms_m | L=3.5:nonincreasing, L=4.0:nonincreasing, L=4.5:nonincreasing | m=2.0:nonincreasing, m=3.25:nonincreasing, m=4.5:nonincreasing | 0.018933 |
| soil_moment_total_abs_peak_Nm | L=3.5:nonincreasing, L=4.0:nondecreasing, L=4.5:nonmonotonic | m=2.0:nondecreasing, m=3.25:nondecreasing, m=4.5:nondecreasing | 3.7608e+06 |
| support_runtime_delta_x_force_rms_N | L=3.5:nonincreasing, L=4.0:nonincreasing, L=4.5:nonincreasing | m=2.0:nonincreasing, m=3.25:nonmonotonic, m=4.5:nondecreasing | 36632 |
| support_runtime_delta_pitch_moment_rms_Nm | L=3.5:nondecreasing, L=4.0:nondecreasing, L=4.5:nondecreasing | m=2.0:nonmonotonic, m=3.25:nondecreasing, m=4.5:nonmonotonic | 1.474e+06 |

Proxy end-stop reaction values are retained only in machine-readable and CSV proxy_only columns. They are not interpreted here as impact or safety response.
