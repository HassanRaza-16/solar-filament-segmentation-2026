# Solar Filament Segmentation 2026

A hybrid deep-learning approach for instance segmentation of solar filaments in GONG H-alpha observations.

## Project Overview

This project was developed for the **Solar Filament Segmentation Challenge 2026**, organized by the Earth-Space AI Research (ESAIR) Lab.

The objective is to detect and segment individual solar filaments in H-alpha solar images.

The final approach combines two models:

- **U-Net with ResNet34 encoder:** produces pixel-level filament segmentation.
- **YOLO11s-seg:** detects individual filament instances.
- **Hybrid fusion:** combines predictions from both models with post-processing to generate instance masks.

## Results

| Evaluation | Result |
|---|---:|
| Cross-fitted validation PQ | 0.3916 |
| Improvement over U-Net-only baseline | +0.0338 |
| Kaggle public leaderboard score | 0.35 |
| Previous personal best | 0.30 |

The validation and public leaderboard results come from different evaluation sets and should not be directly compared.

## Model Checkpoints

The trained model checkpoints are:

- `unet_resnet34.pt` — trained U-Net model.
- `detector_best.pt` — best YOLO11s-seg detector checkpoint.

## Repository Structure

```text
solar-filament-segmentation-2026/
├── README.md
├── requirements.txt
├── notebooks/
├── checkpoints/
├── logs/
├── results/
└── report/
```

The folders will be populated with the corresponding notebooks, model weights, training logs, results, and technical report.

## Training and Inference

The models were trained using Kaggle GPU resources.

The project includes separate training and inference workflows. The inference workflow performs model prediction, fusion, post-processing, and generation of the competition submission CSV.

The competition submission uses the required columns:

- `filament_id`
- `segmentation_rle`

The masks are encoded for the original 2048 × 2048 image dimensions.

## Acknowledgements and Attribution

This project uses and builds upon the publicly available implementation:

**Original repository:**  
https://github.com/ameyypawar/filament-seg

Credit is given to the original author for the underlying implementation and workflow. The training, model checkpoints, validation experiments, fusion evaluation, and submission results documented here correspond to this project.

Please consult the original repository's licensing terms before redistributing its source code.

## Technical Report

The four-page technical report documents the methodology, training experiments, validation results, limitations, and project contributions.

The report will be added to the `report/` directory.

## Disclaimer

This project is an experimental computer-vision approach for solar filament segmentation. Reported results are specific to the competition evaluation and do not establish scientific or operational performance outside that setting.
