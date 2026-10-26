# MobileSAM Multi-Image Pilot QA Summary

## 1. Project Overview

- Project: Smart Agriculture Data Labeling
- Model: MobileSAM (vit_t)
- Method: Point-Prompt AI-Assisted Segmentation
- Pilot Images: 5
- Positive Point Prompts: 7
- Evaluation Status: PROVISIONAL

## 2. Average Performance

- Mean IoU: 0.7054
- Mean Dice: 0.8089
- Mean Precision: 0.9457
- Mean Recall: 0.7368

## 3. Key Findings

1. Precision was relatively high across the pilot images.
2. Recall varied substantially between images.
3. Small or partially separated plant regions were
   more difficult to capture with a single point prompt.
4. Prompt placement and prompt count affected segmentation.

## 4. Prompt Improvement Experiment

- Target Image: ave-0032-0006.jpg
- Baseline IoU: 0.3379
- Improved IoU: 0.5161
- IoU Change: +0.1782

The improved experiment used two independent point prompts
and combined the resulting masks.

## 5. Evaluation Limitations

- Label ID mapping has not been fully verified.
- Label ID 255 was provisionally treated as an ignore region.
- All other nonzero IDs were provisionally treated as foreground.
- Point prompts were manually selected.
- This is an exploratory five-image pilot, not an independent
  benchmark or a fully automatic labeling evaluation.

## 6. Next Steps

1. Verify reference label mapping.
2. Convert predicted masks to polygons.
3. Perform human QA and polygon correction.
4. Validate final annotation exports.
