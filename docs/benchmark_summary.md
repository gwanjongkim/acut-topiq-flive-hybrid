# Benchmark Summary — A-CUT TOPIQ + FLIVE Hybrid Technical IQA

## Overview
- **Repository**: `acut-topiq-flive-hybrid`
- **Role in A-CUT**: Best Offline / Log-Only Technical IQA Candidate (Official SRCC 0.8069)
- **Task**: Hybrid Technical Image Quality Assessment Fusion

## Evaluated Metrics

| Fusion Variant | Official 4,967 SRCC | Common Split SRCC | MAE | Severe FP | Decision |
| :--- | :---: | :---: | :---: | :---: | :--- |
| `topiq_flive_60_40` | **0.8069** | 0.8218 | 5.08 | 3 | **Best Log-Only Candidate** |
| `topiq_existing_flive_57_43` | 0.8065 | **0.8222** | **5.04** | 3 | Grid Optimum |
| `production_existing` (Baseline) | 0.7168 | 0.7036 | 12.00 | **0** | Production |

## Key Engineering & Audit Findings

- **+0.090 SRCC Gain Over Production Baseline**: Raising overall SRCC from `0.7168` to `0.8069` and cutting MAE from `12.00` to `5.04`.
- **Deployment Gate**: Designated as the primary log-only shadow candidate (`results/signal_recommendation.json`) pending on-device severe-FP gating verification.

## Evidence Files in `results/`
All metric tables, per-sample predictions, parity checks, and audit reports backing the numbers above are stored directly in the [`results/`](../results/) directory of this repository.
