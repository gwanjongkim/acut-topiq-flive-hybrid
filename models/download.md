# Model Artifacts — A-CUT TOPIQ + FLIVE Hybrid Technical IQA

## Included in Repository (`models/model_files/`)
- `Uses `topiq_lite_mixed112_frozen_fp16.tflite` (in `acut-topiq-mixed112`) + `flive_image_mobile.tflite` (in `acut-technical-iqa`)`

## Notes on Large Checkpoints (>50 MB)
- Mobile TFLite deliverables under 50 MB are committed directly inside `models/model_files/`.
- Any artifact exceeding GitHub's 50 MB / 100 MB git blob limit (such as `icaa_dat_tf_native_fp16.tflite` at 167.74 MB) is attached to this repository's **GitHub Releases** page.
