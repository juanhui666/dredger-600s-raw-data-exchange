# Dredger Raw Simulation Data Exchange

This repository contains retained simulation inputs, time histories, and a separately identified 600 s case-data package.

## Current Repaired 600 s RAC Evidence

For the repaired spud-soil contact-point kinematics, start here:

- [`paper_evidence/600s_support_system_contact_kinematics_repair_rac_v19_2026-07-19/`](paper_evidence/600s_support_system_contact_kinematics_repair_rac_v19_2026-07-19/)

This package contains the shared input, run status, neutral metrics, accepted-corrector trace, seals, engineering-review record, and lossless chunks of the complete raw result. It covers one RAC case only and is not a 14-case parameter study.

The earlier 18-case package and its compact exchange remain available as historical records of the incomplete soil-X mapping:

- [`paper_exchange/current_600s_support_system/`](paper_exchange/current_600s_support_system/)
- [`paper_evidence/600s_support_system_soil_x_midpoints_v19_2026-07-19/`](paper_evidence/600s_support_system_soil_x_midpoints_v19_2026-07-19/)

They must not be used as physical evidence for the repaired contact-point model. The older `raw/` and `chunks/` trees are also retained only for traceability.

## Contents

- `raw/baseline_600s/`: the retained 0.1 s response history and exact simulation input for the 600 s baseline.
- `raw/inputs/aqwa/`: the three original AQWA body-load CSV files used by the run.
- `raw/inputs/cutter/`: the original 600 s cutter-load CSV file used by the run.
- `raw/oat_trolley_60s/`: 17 trolley cases, each with its exact input payload and 0.1 s response history.
- `raw/oat_soil_60s/`: 9 spud-soil cases, each with its exact input payload and 0.1 s response history.
- `chunks/`: lossless browser-sized partitions of every CSV. Each part repeats the original header; `DATA_INDEX.json` records row coverage.
- `INDEX.md` and `index/`: small neutral indexes for browser-based readers.

Column names carry the exported units. `DATA_INDEX.json` records source identity, row counts, columns, source SHA-256, exported SHA-256 and chunk ranges. `MANIFEST.json` hashes every published file.

## Transport Rule

CSV files under `raw/` are byte-for-byte copies of the retained source files. Input JSON values are unchanged except that absolute local filesystem paths are replaced by stable `source_ref:` identifiers; the original source SHA-256 is retained in `DATA_INDEX.json`. CSV chunks preserve source data lines exactly and add only a repeated header.

## Excluded

No paper manuscript, literature file, writing prompt, source code, Agent file or local credential is included. The invalidated 1.5 h result is not included.
