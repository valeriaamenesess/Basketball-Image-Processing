# Ball and Player Tracking in Basketball Video Clips: A YOLOv8 Study

This project builds a custom computer vision pipeline for detecting basketball players, referees, and the basketball itself from broadcast basketball footage.

The workflow includes:
- frame extraction from source videos
- automatic annotation using Grounding DINO + AutoDistill
- post-processing of noisy labels
- YOLOv8 training
- inference on unseen videos

The project was developed as part of **31256 Image Processing and Pattern Recognition** at the **University of Technology Sydney**.

## Project Goal

The goal of this project is to train a YOLOv8-based detector that can identify four gameplay entities from basketball broadcast footage:

- `USA Player`
- `Opponent Player`
- `Referee`
- `Basketball`

This repository focuses on the practical pipeline used to:
1. generate the dataset,
2. annotate it automatically,
3. clean the labels,
4. train a YOLO model,
5. test the trained model on new videos.

---

## Dataset

Dataset link:

```text
https://drive.google.com/file/d/1e5QqS9OcaIivUd8F8C1z65qqxypKzMAc/view?usp=sharing