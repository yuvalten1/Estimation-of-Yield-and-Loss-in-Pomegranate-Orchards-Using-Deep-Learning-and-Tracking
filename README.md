# Estimation-of-Yield-and-Loss-in-Pomegranate-Orchards-Using-Deep-Learning-and-Tracking
MSC Thesis - Estimation of Yield and Loss in Pomegranate Orchards Using Deep Learning and Tracking

**Author:** Yuval Tenenboim  
**Supervisors:** Prof. Yael Edan, Dr. Tarin Paz-Kagan 

Dept. of Industrial Engineering & Management, Ben-Gurion University of the Negev

The Jacob Blaustein Institutes for Desert Research, Ben-Gurion University of the Negev, Israel

The repository contains the code developed to support the methodology presented in the thesis, including data preprocessing, synthetic dataset generation, object detection, and tracking-based yield and loss estimation from UAV imagery.

## Thesis Overview

Fruit cracking causes substantial yield losses in pomegranate orchards, yet most vision-based yield estimation systems focus exclusively on counting healthy fruits and ignore losses occurring on the tree or on the ground. This thesis proposes a deep-learning framework for the joint estimation of yield and fruit loss using UAV-acquired RGB video data.

The framework integrates:

Task-specific object detection models for healthy (yield) and defective (loss) fruits

A tracking-by-detection approach for video-based fruit counting

Tree-level yield and loss estimation under commercial orchard conditions

The system was evaluated on UAV video data collected from multiple commercial orchard plots and validated against field-based ground-truth measurements, demonstrating that explicitly modelling fruit loss yields a more realistic and operationally relevant assessment of orchard productivity
