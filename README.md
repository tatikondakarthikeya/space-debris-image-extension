# Space Debris Image-Based Extension

An experimental image-based extension for exploring visual feature extraction and image-plane position prediction from object-detection annotations.

> **Research status: draft / not validated.** This repository is not a production tracker and does not establish real-world orbital trajectory prediction accuracy. Keep it private until the dataset provenance, methodology, and results have been reviewed.

## What is in this repository?

- `notebooks/space_image_extension.ipynb` — notebook for parsing YOLO-format labels, extracting MobileNetV2 image embeddings, combining embeddings with bounding-box features, and experimenting with position prediction.
- `data/README.md` — dataset setup and provenance checklist.
- `requirements.txt` — Python dependencies used by the notebook.

## Experimental workflow

1. Parse train/validation YOLO labels into a tabular representation.
2. Extract MobileNetV2 features from the images.
3. Combine visual features with normalized bounding-box coordinates.
4. Explore a neural-network regressor for next-position estimates.
5. Inspect image-plane errors and plots.

These steps describe the current notebook, not a validated end-to-end tracking system.

## Setup

The notebook was authored around Kaggle paths and may require a compatible TensorFlow build and hardware. Create an isolated environment first:

```bash
python -m venv .venv
source .venv/bin/activate  # Windows: .venv\Scripts\activate
python -m pip install --upgrade pip
pip install -r requirements.txt
```

Install a TensorFlow version supported by your OS/Python version if the unpinned dependency does not resolve. GPU setup is platform-specific.

## Before running

1. Obtain the dataset from its original authorized source and verify the terms for images and annotations.
2. Update `/kaggle/input/...` and `/kaggle/working/...` paths for your environment.
3. Verify the actual image extensions and class-ID mapping; the current parser assumes `.jpg` and defines `['debris', 'satellite']` manually.
4. Run cells in order and confirm intermediate CSV, pickle, and model files exist before loading them later.
5. Recompute all metrics on an appropriate held-out set before reporting results.

## Important limitations

- The notebook creates pseudo `object_id` and `frame_id` values by grouping every five rows. These are not verified identities or chronological frames of the same physical object.
- The notebook derives next-position targets from those pseudo-sequences. Consequently, its trajectory plots and threshold-based “accuracy” must not be interpreted as real tracking or orbital-prediction performance.
- Coordinates are image/bounding-box coordinates, not orbital state vectors. No orbital mechanics propagation is implemented in this extension.
- The notebook contains repeated analysis/training cells and relies on intermediate Kaggle files. It has not been independently executed end-to-end during this review.
- Dataset files, model weights, serialized features, and generated plots are intentionally excluded.

## Dataset, citation, and license

**Not yet complete.** Add the exact dataset title, source URL, version, citation, and license/terms after verifying them. Do not upload the dataset unless its terms explicitly permit redistribution. No code license is asserted by this draft; choose one only after confirming the rights to publish the code and all included material.

## Public-release checklist

- [ ] Add verified dataset source, citation, and license/terms.
- [ ] Replace pseudo-sequences with genuine tracked object IDs and ordered frames, or clearly scope the work to a synthetic demonstration.
- [ ] Make paths configurable and remove assumptions about `.jpg` and class IDs.
- [ ] Run the notebook from a clean environment and record exact versions.
- [ ] Recompute metrics and explain the coordinate system and evaluation split.
- [ ] Add an appropriate project license only after rights review.
