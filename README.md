# Space Debris Image-Based Extension

An image-based extension of the space-debris research workflow. The notebook parses YOLO-format labels, extracts image embeddings using MobileNetV2, combines visual features with bounding-box features, and explores position/trajectory prediction and error analysis.

> **Status:** Research notebook draft. It has not been refactored into a production pipeline or independently reproduced during repository preparation.

## Contents
- `notebooks/space_image_extension.ipynb` — original notebook with execution outputs removed; code cells are preserved.
- `data/README.md` — dataset setup guidance.

## Requirements
Python 3.10–3.11 is a reasonable starting point; TensorFlow compatibility depends on your OS and hardware. Install the listed packages in a virtual environment:

```bash
python -m venv .venv
source .venv/bin/activate  # Windows: .venv\Scripts\activate
pip install -r requirements.txt
```

## Run
1. Download the dataset from its authorized source.
2. Update the notebook's `/kaggle/input/...` and `/kaggle/working/...` paths for your environment.
3. Run cells in order and verify intermediate files exist before downstream cells.
4. Recompute all reported metrics before using them in a paper or portfolio.

## Notes and limitations
- The notebook currently depends on Kaggle-specific paths and intermediate pickle/CSV/model files.
- It creates synthetic `object_id`/`frame_id` groupings in parts of the workflow; verify that these correspond to real temporal sequences before interpreting trajectory results.
- Dataset files, trained weights, generated plots and serialized feature tables are excluded.
- This repository is an extension of the separately published ICSIMA work; add the exact paper citation and clarify the novelty/scope before public release.

## Data, citation and license
Add the dataset citation/license and a project license before making this repository public. No license is asserted by this draft.
