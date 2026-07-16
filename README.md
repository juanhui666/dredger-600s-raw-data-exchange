# Dredger Raw Simulation Data Exchange

This repository contains raw retained simulation inputs and time histories only. It does not contain derived statistics, spectral results, sensitivity conclusions, paper text or an analysis prompt.

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

No paper, literature file, frozen 1.5 h result, 445 MB full binary result, source code, Agent file or local credential is included.
