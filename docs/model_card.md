# Model Card — A-CUT TOPIQ + FLIVE Hybrid Technical IQA

## Model Details
- **Model Name**: A-CUT TOPIQ + FLIVE Hybrid Technical IQA (`acut-topiq-flive-hybrid`)
- **Developer**: Gwanjung Kim (A-CUT Mobile Photo Evaluation & Curation Capstone)
- **Architecture**: Weighted linear fusion (`60% TOPIQ-Lite Mixed112 + 40% FLIVE Image Mobile` or `57/43` grid optimum) combining semantic-aware multi-scale TOPIQ features with FLIVE's authentic distortion sensitivity.
- **Deployment Role**: Best Offline / Log-Only Technical IQA Candidate (Official SRCC 0.8069)

## Tensor Input / Output Contract
- **Input Contract**: Precomputed or live signal predictions from `topiq_lite_mixed112_frozen_fp16.tflite` (`384×384`) and `flive_image_mobile.tflite` (`224×224`)
- **Output Contract**: Fused `[0, 100]` technical quality score
- **Included Model Artifacts**:
  - `Uses `topiq_lite_mixed112_frozen_fp16.tflite` (in `acut-topiq-mixed112`) + `flive_image_mobile.tflite` (in `acut-technical-iqa`)`

## Intended Use
- Designed for on-device or offline photo quality and aesthetics evaluation within the A-CUT smartphone photo selection pipeline.
- Not intended as an uncalibrated standalone medical, forensic, or safety-critical classifier.

## Limitations & Audit Qualifications
- **+0.090 SRCC Gain Over Production Baseline**: Raising overall SRCC from `0.7168` to `0.8069` and cutting MAE from `12.00` to `5.04`.
- **Deployment Gate**: Designated as the primary log-only shadow candidate (`results/signal_recommendation.json`) pending on-device severe-FP gating verification.
