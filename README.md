# Dredger Raw Simulation Data Exchange

This repository contains retained simulation inputs, time histories, and a separately identified 600 s case-data package.

## Current 600 s Paper Exchange

For direct review by a paper mentor or writer, start with the five-file exchange directory:

- [`paper_exchange/current_600s_support_system/`](paper_exchange/current_600s_support_system/)

It contains one README, three neutral CSV tables, and one run-status record. It contains no manuscript outline, trend classification, normalized comparison index, or recommended interpretation.

The full audit archive remains available separately:

- [`paper_evidence/600s_support_system_soil_x_midpoints_v19_2026-07-19/`](paper_evidence/600s_support_system_soil_x_midpoints_v19_2026-07-19/)

The older `raw/` and `chunks/` trees below are retained for traceability. They include a different baseline and 60 s one-at-a-time studies and must not be substituted for the current roll-enabled 14-case dataset.

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

No paper manuscript, literature file, writing prompt, frozen 1.5 h result, 445 MB full binary result, source code, Agent file or local credential is included.
