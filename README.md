# Football Object Detection Using YOLO

Football object detection project trained with Ultralytics YOLOv8 on a Roboflow dataset. The model detects 4 classes in match footage:

- `ball`
- `goalkeeper`
- `referee`
- `soccer-player`

## Overview

This repository contains:

- a training and inference notebook: [`Fooball_detection_yolo.ipynb`](./Fooball_detection_yolo.ipynb)
- dataset configuration: [`data.yaml`](./data.yaml)
- Roboflow dataset metadata: [`README.dataset.txt`](./README.dataset.txt) and [`README.roboflow.txt`](./README.roboflow.txt)
- demo outputs in `predict3/` and `predict4/`

The project is set up for football/soccer match analysis, where the detector can be used for player tracking, ball tracking, referee tracking, and broadcast analytics.

## Model

- Base model: `yolov8n.pt`
- Framework: Ultralytics YOLOv8
- Task: Object detection
- Input size: `416x416`
- Training epochs: `20`
- Dataset format: YOLOv8

The notebook shows training and resume workflows using the Ultralytics `YOLO` API, including loading a pretrained YOLOv8n checkpoint and continuing from a saved checkpoint.

### Classes

The detector is trained to recognize 4 classes:

| Class | Description |
| --- | --- |
| `ball` | Match ball |
| `goalkeeper` | Goalkeeper |
| `referee` | Match referee |
| `soccer-player` | Outfield player |

## Dataset

Dataset source:

- Roboflow project: [Smart Football Object Detection](https://universe.roboflow.com/smart-football-object-detection/smart-football-object-detection/dataset/11)
- Version: `11`
- License: `CC BY 4.0`

Dataset summary:

- Total images: `12,820`
- Export format: YOLOv8
- Preprocessing:
  - auto-orientation
  - resize to `640x640` stretch
  - auto-contrast
- Augmentation:
  - horizontal flip
  - vertical flip
  - 90-degree rotations
  - random rotation between `-30` and `+30` degrees
- Bounding-box transforms:
  - horizontal flip
  - vertical flip
  - 90-degree rotations
  - random rotation between `-15` and `+15` degrees
  - brightness adjustment between `-25%` and `+25%`

### `data.yaml`

The dataset config points to:

- `train: /content/train/images`
- `val: /content/valid/images`
- `test: /content/test/images`

And maps the 4 classes listed above.

## Demo

The demo below is a GIF generated from `predict4` using the clip from **second 6 to second 16** so it can render directly inside GitHub README pages.

<p align="center">
  <img src="assets/predict4_6s_16s.gif" alt="Football detection demo" />
</p>

### Demo source

- Source video: `predict4/(1815) FULL MATCH _ Manchester City v Liverpool _ Quarter-Final _ Emirates FA Cup 2025-26 - YouTube and 6 more pages - Personal - Microsoft_ Edge 2026-04-16 20-29-46.avi`
- GIF range: `00:06` to `00:16`

## Project Files

- [`Fooball_detection_yolo.ipynb`](./Fooball_detection_yolo.ipynb) - notebook for training and inference
- [`data.yaml`](./data.yaml) - dataset config
- [`predict3/`](./predict3/) - sample prediction output
- [`predict4/`](./predict4/) - video demo output
- [`assets/predict4_6s_16s.gif`](./assets/predict4_6s_16s.gif) - README demo GIF

## Reproduce

1. Install dependencies:

```bash
pip install ultralytics opencv-python-headless pillow
```

2. Open the notebook:

```bash
jupyter notebook Fooball_detection_yolo.ipynb
```

3. Update paths if you are not using Google Colab-style `/content/...` folders.

## Notes

- The dataset in this repo comes from Roboflow and is licensed under `CC BY 4.0`.
- The demo GIF is intentionally resized for README performance.
- If you retrain the model, you can replace the GIF with a new clip exported from `predict4`.
