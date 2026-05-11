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
```

## How to run the repository

1. Clone the repository:

```bash
git clone <repo-url>
cd Basketball-Image-Processing
```

2. Download the `autoAnnotations.zip` file from the link above.

3. Extract the folder named `autoAnnotations` into the `dataset` folder (at the same level as `yolo_training`).
   - You may delete the `vis_color_clean` folders if you want.

4. Review all 5 Python scripts and change any file paths inside them so they work for your setup.

5. Recreate the virtual environment and install dependencies:

```bash
python -m venv venv
source venv/bin/activate   # Mac/Linux
# venv\Scripts\activate  # Windows
pip install -r requirements.txt
```

6. Run script 1:

```bash
python 1-ExtractFromYT.py
```

   - This will generate all frames into `dataset/images`.

7. Open the `dataset/images` folder in your file explorer and manually delete irrelevant frames (e.g. Olympics graphics at the end).

8. Run script 2:

```bash
python 2-AutoAnnotation.py
```

   - This will perform auto annotation using AutoDistill and Grounding DINO. It may take several hours on an RTX 3070.

9. Run script 3:

```bash
python 3-BoxPostprocessing.py
```

   - This postprocessing script fixes some issues from the predictions produced by script 2.

10. Run script 4:

```bash
python 4-YOLOmodel.py
```

   - This trains the YOLO model. At 50 epochs, it takes about 5 hours on a 3070 (~10 epochs/hour).

11. Run script 5:

```bash
python 5-LiveTest.py
```

   - This tests the model on a video of your choice. It will create an MP4 so you can watch the results.

