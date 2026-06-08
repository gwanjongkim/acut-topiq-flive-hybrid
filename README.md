# A-CUT TOPIQ + FLIVE Hybrid

#### A-CUT Capstone Project — Mobile Image Quality and Aesthetic Assessment

> Hybrid model utilizing TOPIQ and FLIVE (topiq_existing_flive_57_43).

## Introduction

Hybrid model utilizing TOPIQ and FLIVE signals, specifically the 60/40 ratio variant. It was identified as the best performing candidate under the official benchmark protocol.

- **Role**: Best official log-only candidate.
- **Task**: Image Quality and Aesthetic Assessment.

## Model / Method

Combines signals from TOPIQ and FLIVE models. This hybrid approach significantly outperforms the existing production baseline on the official protocol, though it is currently restricted to log-only profiling.

- **Artifacts**: Inferred from scripts

## Dataset and Benchmark

- Benchmark results are summarized below. See `docs/benchmark_summary.md` for detailed per-dataset analysis.
- Note: Large datasets are excluded due to size/license constraints.

## Model Weights / Artifacts

- Due to size constraints, artifacts larger than 50MB are not included in this repository.
- Recommended hosting: GitHub Releases.
- See `models/download.md`.

## Repository Structure

```
.
├── configs/
├── docs/
├── models/
├── results/
├── scripts/
└── requirements.txt
```

## Requirements

Please refer to `requirements.txt`. Minimal dependencies include `torch`, `tensorflow`, `numpy`, and `pillow`.

## Quick Start

```bash
pip install -r requirements.txt
python scripts/benchmark_student_flive_hybrid_20260604.py
```
*(Verify path assumptions in `docs/reproduction_notes.md`)*

## Results

| Dataset | Metric | Value | Evidence Path | Decision |
|---------|--------|-------|---------------|----------|
| Official Protocol | topiq_flive_60_40 SRCC | 0.8069 | outputs/official_protocol_technical_signal_benchmark_20260604/report.md | Log-Only |
| Official Protocol | topiq_flive_60_40 PLCC | 0.8694 | outputs/official_protocol_technical_signal_benchmark_20260604/report.md | Log-Only |
| Official Protocol | topiq_flive_60_40 MAE | 7.62 | outputs/official_protocol_technical_signal_benchmark_20260604/report.md | Log-Only |

## Limitations

- Results are based on local reproduction and may not exactly match original papers.
- See `docs/model_card.md` for detailed limitations.

## Citation

```bibtex
@misc{acut_topiq_flive_2026,
  title        = {A-CUT TOPIQ + FLIVE Hybrid: Mobile Image Quality and Aesthetic Assessment Model},
  author       = {Kim, Gwanjung},
  year         = {2026},
  note         = {Capstone project repository}
}
```
### Original References

- A-CUT Technical IQA Signal Benchmark (2026)

## Related Repositories

- [A-CUT Public Model Repositories](..)
