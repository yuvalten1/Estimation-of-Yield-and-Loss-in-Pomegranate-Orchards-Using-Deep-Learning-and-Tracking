<h1 align="center"> Estimation-of-Yield-and-Loss-in-Pomegranate-Orchards-Using-Deep-Learning-and-Tracking </h1>
MSC Thesis - Estimation of Yield and Loss in Pomegranate Orchards Using Deep Learning and Tracking

<p align="center">
 <img width="431" height="689" alt="image" src="https://github.com/user-attachments/assets/5bb5dcc8-5024-4944-91c0-11ffa0c5105d" />
</p>

<h4 align="center"> Author: Yuval Tenenboim  </h4>
<h4 align="center"> Supervisors: Prof. Yael Edan, Dr. Tarin Paz-Kagan </h4>

<h4 align="center"> Dept. of Industrial Engineering & Management, Ben-Gurion University of the Negev </h4>

<h4 align="center"> The Jacob Blaustein Institutes for Desert Research, Ben-Gurion University of the Negev, Israel </h4>



 The repository contains the datasets and code developed to support the methodology presented in the thesis, including data preprocessing, object detection, and tracking-based yield and loss estimation from UAV imagery.

 


## Thesis Overview

Fruit cracking causes substantial yield losses in pomegranate orchards, yet most vision-based yield estimation systems focus exclusively on counting healthy fruits and ignore losses occurring on the tree or on the ground. This thesis proposes a deep-learning framework for the joint estimation of yield and fruit loss using UAV-acquired RGB video data.

The framework integrates:

- Task-specific object detection models for healthy (yield) and defective (loss) fruits

- A tracking-by-detection approach for video-based fruit counting

- Tree-level yield and loss estimation under commercial orchard conditions

The system was evaluated on UAV video data collected from multiple commercial orchard plots and validated against field-based ground-truth measurements, demonstrating that explicitly modelling fruit loss yields a more realistic and operationally relevant assessment of orchard productivity.


## Notebook Contents

The notebook (`Estimation_Pomegranate_notebook.ipynb`) provides an end-to-end experimental pipeline used in the thesis, from dataset preparation to final yield/loss estimation evaluation.

It includes the following stages:

### 1. Environment setup (Google Colab)
- Mounting Google Drive for data and results storage
- Installing required packages (Ultralytics/YOLO, tracking libraries, supervision, etc.)

### 2. Dataset download and organization
- Downloading annotated datasets from Roboflow
- Renaming and organizing dataset versions
- Creating separate datasets for:
  - **Yield (healthy fruits)**
  - **Loss (defective/cracked fruits)**
  - **Joint yield + loss**
- Label cleanup and class remapping for task-specific training

### 3. Dataset preprocessing and augmentation
- Image preprocessing (including contrast enhancement / normalization steps)
- Data augmentation for training robustness (noise, blur, and additional transforms)
- Expansion of training sets with extra orchard images (including red tape presence examples)

### 4. Fine-tuning and training object detection models
- Fine-tuning YOLO-based models
- Training multiple model configurations:
  - Joint model (healthy + defective)
  - Yield-only model
  - Loss-only model
- Saving training outputs and checkpoints
- 
<img width="629" height="657" alt="image" src="https://github.com/user-attachments/assets/0aac9ea6-d8c1-4815-ba5a-99bad60f7fe5" />

### 5. Tiling-based training workflow
- Creating tiled datasets to improve small-object detection in UAV imagery
- Training tiled detection models, especially for defective fruit detection

### 6. Inference and visualization
- Loading trained / pre-trained models
- Running predictions on validation/test images and videos
- Visualizing detections for qualitative inspection

### 7. Detection performance evaluation
- Confusion matrix generation and visualization (including normalized confusion matrices)
- Metric calculations derived from detection results (for yield, loss, and joint models)

### 8. Synthetic dataset creation and transfer-learning experiments
- Synthetic data preparation workflow
- Segmentation-based processing using SAM (Segment Anything Model)
- Creation of additional transfer-learning datasets from segmented objects/scenes

### 9. Tracking and video-based counting
- SORT-based tracking pipeline for counting fruits across UAV video frames
- Video preparation for validation
- Tracking runs across measuring trees sequences

  <img width="1037" height="385" alt="image" src="https://github.com/user-attachments/assets/6c62fe19-88ed-41e9-8d04-d034fe6f68b6" />


### 10. Yield and loss estimation evaluation
- Aggregation of detection/tracking outputs into tree-level and plot-level estimates
- Comparison against ground-truth field measurements
- Regression/error analysis and visualization for:
  - Predicted yield vs. true yield
  - Predicted loss vs. true loss
  - Estimation error distributions and combined performance analysis

## Notes
- The notebook is designed as a **research workflow notebook**, combining preprocessing, training, inference, tracking, and evaluation in a single place.
- Several paths and commands are configured for **Google Colab + Google Drive** usage and may require adaptation for local execution.
- Some cells are experimental/iterative and were used to compare multiple model and preprocessing variants during thesis development.
