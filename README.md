# Human & Robot Detection — YOLOv8 Weights

Pre-trained YOLOv8 model weights for detecting **humans and robots**. This is the YOLOv8 variant of the human-robot detection project, offering a lighter and faster model compared to the YOLOv7 version.

---

## Overview

This model was fine-tuned from the [Ultralytics YOLOv8](https://github.com/ultralytics/ultralytics) architecture on a custom dataset of humans and industrial robots. It targets the same use case as the YOLOv7 companion model but takes advantage of YOLOv8's improved speed-accuracy trade-off and simpler inference API.

| Class   | Label |
|---------|-------|
| Human   | `0`   |
| Robot   | `1`   |

---

## Repository Contents

| File              | Description                                      |
|-------------------|--------------------------------------------------|
| `yolov8_best.pt`  | Best checkpoint from custom training (~6 MB)     |

> The full training pipeline lives in the companion repo: [human_and_robot](https://github.com/Stanley-LinSY/human_and_robot)

---

## Requirements

```bash
pip install ultralytics
```

---

## Usage

### Download Weights

```bash
git clone https://github.com/Stanley-LinSY/human_and_robot_yolov8_weight_only
```

### Run Inference (Python)

```python
from ultralytics import YOLO

model = YOLO('yolov8_best.pt')

# On an image
results = model('path/to/image.jpg', conf=0.25)
results[0].show()

# On a video
results = model('path/to/video.mp4', conf=0.25, save=True)

# On webcam
results = model(0, conf=0.25, show=True)
```

### Run Inference (CLI)

```bash
yolo detect predict model=yolov8_best.pt source=path/to/image.jpg conf=0.25
```

---

## Model Details

| Property        | Value            |
|-----------------|------------------|
| Base Model      | YOLOv8           |
| Classes         | 2 (Human, Robot) |
| Framework       | Ultralytics      |
| Weight Format   | `.pt`            |
| File Size       | ~6 MB            |

---

## Comparison with YOLOv7 Version

| Feature        | YOLOv7                  | YOLOv8 (this repo)         |
|----------------|-------------------------|----------------------------|
| Weight Size    | ~12 MB                  | ~6 MB                      |
| Inference API  | Custom detect.py script | `ultralytics` pip package  |
| Speed          | Fast                    | Faster                     |

---

## Related Repositories

- [human_and_robot](https://github.com/Stanley-LinSY/human_and_robot) — Full training pipeline and notebooks
- [robot_and_human_yolov7_weights_only](https://github.com/Stanley-LinSY/robot_and_human_yolov7_weights_only) — YOLOv7 version of this model
