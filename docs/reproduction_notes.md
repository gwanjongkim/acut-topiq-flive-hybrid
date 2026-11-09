# Reproduction & Execution Notes — A-CUT TOPIQ + FLIVE Hybrid Technical IQA

## Environment Setup
```bash
python3 -m venv .venv
source .venv/bin/activate
pip install --upgrade pip
pip install -r requirements.txt
```

## Available Scripts (`scripts/`)
```bash
python scripts/benchmark_technical_iqa_signals_20260604.py --help
```

## Preprocessing & Parity Verification
- **Input Specification**: Precomputed or live signal predictions from `topiq_lite_mixed112_frozen_fp16.tflite` (`384×384`) and `flive_image_mobile.tflite` (`224×224`)
- **Output Specification**: Fused `[0, 100]` technical quality score
- Ensure EXIF orientation transposition (`ImageOps.exif_transpose`) is applied prior to resizing so portrait smartphone photos are not evaluated rotated.
