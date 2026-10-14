# Review notes — Space Debris Image-Based Extension

Review performed against the staged notebook source on 2026-10-14. This is a static source review; the notebook was not executed end-to-end.

## Findings

1. **Synthetic sequence construction (high):** code groups rows into pseudo objects using `df.index // 5` and creates frame IDs by row order. This does not establish object identity or temporal order. Any next-position score based on these values is not evidence of real trajectory tracking.
2. **Coordinate interpretation (high):** features are normalized image/bounding-box coordinates; the extension does not implement orbital-state estimation or orbital mechanics propagation.
3. **Dataset assumptions (medium):** the parser hard-codes `.jpg` and class names. Verify image extension, class IDs, annotation format, and dataset split before training.
4. **Environment portability (medium):** paths are hard-coded to `/kaggle/input` and `/kaggle/working`; intermediate files are expected to exist across cells.
5. **Provenance/license (release blocker):** dataset source/citation/license and project code license remain unverified.

## Recommended interpretation

Treat this as a notebook prototype for image features and synthetic image-plane position experiments. Do not advertise it as a validated orbital trajectory prediction or operational space-debris tracking system until genuine temporal data, leakage-safe splits, a meaningful baseline, and reproducible evaluation are implemented.
