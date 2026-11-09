# A-CUT TOPIQ + FLIVE Hybrid Technical IQA

> **A-CUT Best Log-Only Shadow Technical IQA Candidate — 60/40 Hybrid Fusion of TOPIQ-Lite and FLIVE Image Mobile**

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](./LICENSE)
[![Project: A-CUT](https://img.shields.io/badge/Project-A--CUT%20Capstone-success.svg)](https://github.com/gwanjongkim/photo_score_project)

## 1. Overview

- **Role in A-CUT**: Best Offline / Log-Only Technical IQA Candidate (Official SRCC 0.8069)
- **Task**: Hybrid Technical Image Quality Assessment Fusion
- **Architecture**: Weighted linear fusion (`60% TOPIQ-Lite Mixed112 + 40% FLIVE Image Mobile` or `57/43` grid optimum) combining semantic-aware multi-scale TOPIQ features with FLIVE's authentic distortion sensitivity.

## 2. Input / Output Contract & Model Artifacts

- **Input Contract**: Precomputed or live signal predictions from `topiq_lite_mixed112_frozen_fp16.tflite` (`384×384`) and `flive_image_mobile.tflite` (`224×224`)
- **Output Contract**: Fused `[0, 100]` technical quality score
- **Model Files (`models/model_files/` & Releases)**:
  - `Uses `topiq_lite_mixed112_frozen_fp16.tflite` (in `acut-topiq-mixed112`) + `flive_image_mobile.tflite` (in `acut-technical-iqa`)`

## 3. Benchmark Results

| Fusion Variant | Official 4,967 SRCC | Common Split SRCC | MAE | Severe FP | Decision |
| :--- | :---: | :---: | :---: | :---: | :--- |
| `topiq_flive_60_40` | **0.8069** | 0.8218 | 5.08 | 3 | **Best Log-Only Candidate** |
| `topiq_existing_flive_57_43` | 0.8065 | **0.8222** | **5.04** | 3 | Grid Optimum |
| `production_existing` (Baseline) | 0.7168 | 0.7036 | 12.00 | **0** | Production |

## 4. Key Engineering Notes & 2026 Audit Findings

- **+0.090 SRCC Gain Over Production Baseline**: Raising overall SRCC from `0.7168` to `0.8069` and cutting MAE from `12.00` to `5.04`.
- **Deployment Gate**: Designated as the primary log-only shadow candidate (`results/signal_recommendation.json`) pending on-device severe-FP gating verification.

## 5. Quick Start

```bash
pip install -r requirements.txt
python scripts/benchmark_technical_iqa_signals_20260604.py --help
```

For full documentation, see:
- [`docs/model_card.md`](./docs/model_card.md) — Architecture, tensor contracts, and limitations
- [`docs/benchmark_summary.md`](./docs/benchmark_summary.md) — Detailed metrics and dataset evaluations
- [`docs/reproduction_notes.md`](./docs/reproduction_notes.md) — Environment and reproduction guide
- [`models/download.md`](./models/download.md) — Model binary hashes and download notes

## 6. A-CUT Ecosystem Repositories

| Repository | Dimension | Role / Status | Key Metric |
| :--- | :---: | :--- | :--- |
| [acut-nima-mobile](https://github.com/gwanjongkim/acut-nima-mobile) | Aesthetic (IAA) | **Production Ensemble (0.40)** | AVA SRCC `0.5894`, AUC `0.8018` |
| [acut-rgnet-mobile](https://github.com/gwanjongkim/acut-rgnet-mobile) | Aesthetic (IAA) | **Production Ensemble (0.45)** | AADB SRCC `0.6819` (FP16 `0.6648`) |
| [acut-mobile-alamp](https://github.com/gwanjongkim/acut-mobile-alamp) | Aesthetic (IAA) | **Production Ensemble (0.15)** | AVA Acc `0.7633`, AUC `0.7877` |
| [acut-icaa-color-aesthetics](https://github.com/gwanjongkim/acut-icaa-color-aesthetics) | Color Aesthetics | **Verified TF-Native Port** | ICAA17K Color SRCC `0.8791`, MOS `0.9058` |
| [acut-koniq-flive-technical-iqa](https://github.com/gwanjongkim/acut-koniq-flive-technical-iqa) | Technical (IQA) | **Production Baseline (4/7 + 3/7)** | Official SRCC `0.7168` (`0.7958` recon), `0` Severe FP |
| [acut-technical-iqa](https://github.com/gwanjongkim/acut-technical-iqa) | Technical (IQA) | **Umbrella Benchmark** | 4,967-Image Official Protocol Suite |
| [acut-topiq-mixed112](https://github.com/gwanjongkim/acut-topiq-mixed112) | Technical (IQA) | **Evaluated Candidate** | SPAQ SRCC `0.8990`, KonIQ `0.8630` |
| [acut-topiq-flive-hybrid](https://github.com/gwanjongkim/acut-topiq-flive-hybrid) | Technical (IQA) | **Best Log-Only Shadow (60/40)** | Official SRCC `0.8069`, MAE `5.04` |
| [acut-c6-topiq-koniq](https://github.com/gwanjongkim/acut-c6-topiq-koniq) | Technical (IQA) | **Negative Result (Rejected)** | Official SRCC `0.7314`, MAE `15.39` |
| [acut-mdiqa-benchmark](https://github.com/gwanjongkim/acut-mdiqa-benchmark) | Technical (IQA) | **Teacher Ceiling Reference** | KonIQ SRCC `0.9464`, SPAQ `0.9136` |
| [acut-musiq-probe](https://github.com/gwanjongkim/acut-musiq-probe) | Technical (IQA) | **Reference & Probe Study** | Official SPAQ `0.9460`, KonIQ `0.9275` |
| [acut-student-iqa](https://github.com/gwanjongkim/acut-student-iqa) | Technical (IQA) | **Distillation Study (No-Go)** | 14k Student SRCC `0.7436`, SPAQ `0.8984` |
| [photo_score_project](https://github.com/gwanjongkim/photo_score_project) | Full Monorepo | **Core Research Workspace** | Complete Training, Audit & Pipeline Code |

## 7. References & Citation

- Chen et al. (2024), *TOPIQ*, IEEE TIP.
- Ying et al. (2020), *PaQ-2-PiQ (FLIVE)*, CVPR.

```bibtex
@misc{acut_topiq_flive_hybrid_2026,
  title        = {A-CUT TOPIQ + FLIVE Hybrid Technical IQA: A-CUT Best Log-Only Shadow Technical IQA Candidate — 60/40 Hybrid Fusion of TOPIQ-Lite and FLIVE Image Mobile},
  author       = {Kim, Gwanjung},
  year         = {2026},
  howpublished = {\url{https://github.com/gwanjongkim/acut-topiq-flive-hybrid}}
}
```
