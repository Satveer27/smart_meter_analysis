# Smart Meter Analysis

An empirical study of **how accurately software power meters and consumer smart plugs measure real energy consumption**. The project collects experimental power data across multiple tools, hardware platforms and load conditions, then cleans, aggregates and compares it with statistical methods in Python.

**📄 Read the full write-up: [Honours Individual Project dissertation (PDF)](dissertation.pdf)**, University of Glasgow, supervised by Yehia Elkhatib.

## Overview

Software power meters (HWiNFO, Open Hardware Monitor, AMD uProf, Intel Power Gadget, nvidia-smi) report CPU/GPU power draw without dedicated hardware, but how much can you trust them? This project answers that by running controlled, repeatable experiments and comparing the tools against each other, and comparing smart plugs against traditional meters.

It has four parts:

| Study | Question | Folder |
|---|---|---|
| **Software meters, Intel** | How closely do software tools agree on an Intel CPU laptop? | [`experiment_data_intel`](experiment_data_intel) |
| **Software meters, AMD** | Do the same findings hold on an AMD CPU laptop? | [`experiment_data_amd`](experiment_data_amd) |
| **Smart vs traditional meters** | How does a Kasa smart plug compare with a traditional meter on household appliances? | [`smart_and_trad_results`](smart_and_trad_results) |
| **Usability testing** | How did users rate the usability of the tools (Likert survey)? | [`usability_testing_results`](usability_testing_results) |

## Key findings

- **Smart plugs beat traditional meters.** Across kettle, rice cooker, toaster, smartwatch and laptop tests, the Kasa smart plug gave more stable, accurate readings. It also tracked fluctuations in real time and supports data logging. The traditional meter struggled at low loads and produced step-like readings.
- **HWiNFO is more accurate than Open Hardware Monitor (OHM).** Against hardware-backed baselines (Intel Power Gadget, AMD uProf, nvidia-smi), HWiNFO had lower RMSE in both CPU and GPU tests. In one case, for example, it scored about 0.076 versus OHM's 0.083. OHM's deviation grew under heavy load.
- **Results depend on the platform.** On AMD, both software tools closely tracked uProf. On Intel, they struggled to reproduce the Intel Power Gadget distribution.
- **HWiNFO is also easier to use.** In a usability study with 20 participants (half technical, half non-technical), HWiNFO scored higher on every dimension of a TAM-based survey. Every OHM user failed at least one task, mostly because of missing features such as logging.

## Method

- **Controlled load states:** idle, gaming, CPU stress (5 / 10 / 15 processes at varying priority), memory stress (1000 MB threshold at 250 / 500 / 750 MB/s), and GPU stress (Furmark, HeavyLoad).
- **Repeatability:** each test runs 3 times for 5 minutes. The runs are concatenated into a 15-minute dataset per tool and load.
- **Data collection:** HWiNFO logging, a custom Python logger for Open Hardware Monitor (via `pythonnet`), `nvidia-smi` CLI logging, AMD uProf, and Intel Power Gadget.
- **Smart plug data:** pulled from a Kasa server. Traditional meter readings are extracted from video using an OpenAI vision model on frames stored in S3 (OCR pipeline).
- **Usability study:** 20 participants, a TAM-based Likert survey and task-based evaluation of HWiNFO versus OHM.
- **Analysis:** RMSE between tools, time-series plots, Gaussian distribution fits and cumulative distribution (CDF) comparisons.

## Tech stack

Python 3.10 · pandas · NumPy · SciPy · Matplotlib · Jupyter · OpenCV · pytesseract · OpenAI API · AWS S3 (boto3) · pythonnet

## Repository layout

```
smart_meter_analysis/
├── experiment_data_intel/        # Intel laptop: raw logs, cleaned data, notebooks, failed-run archives
│   ├── extract_data_ohm.ipynb    #   live logger for Open Hardware Monitor
│   └── clean_and_visualise.ipynb #   cleaning, aggregation, plots, RMSE
├── experiment_data_amd/          # AMD laptop: same methodology
│   ├── all_experiment_data/      #   raw per-run logs (HWiNFO, OHM, uProf, nvidia-smi)
│   ├── amd_overall_experiments*/ #   cleaned, aggregated CPU and GPU data
│   └── clean_and_visualise.ipynb
├── smart_and_trad_results/       # Smart plug vs traditional meter on household appliances
│   ├── extract_data_trad.ipynb   #   video → frames → LLM OCR → CSV
│   └── clean_and_visualise.ipynb
└── usability_testing_results/    # Survey results and Likert bar charts
```

## Getting started

```bash
git clone <repo-url>
cd smart_meter_analysis
pip install pandas numpy scipy matplotlib jupyter
```

Open the `clean_and_visualise.ipynb` notebook in the study you want and run the cells in order. Every cell has a markdown description. Each folder has its own `readme.md` with the extra dependencies it needs:

- `pythonnet` for live Open Hardware Monitor logging
- `opencv-python`, `pytesseract`, `openai` and `boto3` for the video extraction notebook, which also needs your own OpenAI key and video files (not included in the repo)

Tested on Windows 10 with Python 3.10.8.

## Notes

- The repository ships the full dataset (about 800 files), so the notebooks can be run without repeating the experiments.
- `experiment_data_intel/archives` holds earlier experiments kept for reference only.
