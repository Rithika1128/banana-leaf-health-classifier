
#  Banana Leaf Health Classifier

A computer vision project for classifying banana leaf diseases using traditional machine learning and deep learning approaches.

## 📌 Project Overview

Banana leaf diseases can affect crop health, quality, and yield. This project explores image-based classification of banana leaf diseases using two different approaches:

- **HOG + Support Vector Machine (SVM)**
- **MobileNetV2 Transfer Learning**

The objective was to compare handcrafted image features with learned deep visual features and evaluate their classification performance.

## 📊 Dataset

The dataset contains **408 images** belonging to **7 classes**:

| Class | Images |
|---|---:|
| Banana Healthy Leaf | 86 |
| Banana Insect Pest Disease | 86 |
| Banana Black Sigatoka Disease | 67 |
| Banana Moko Disease | 55 |
| Banana Bract Mosaic Virus Disease | 50 |
| Banana Panama Disease | 41 |
| Banana Yellow Sigatoka Disease | 23 |

The dataset is imbalanced, with Banana Yellow Sigatoka Disease having the fewest images.

## 🔧 Data Preprocessing

- Checked images for corrupted or unreadable files
- Resized images according to the selected model
- Used **128 × 128** images for HOG + SVM
- Used **224 × 224** images for MobileNetV2
- Applied MobileNetV2 preprocessing
- Used a **stratified train-validation-test split** to maintain class proportions

### Dataset Split

- Training: **285 images**
- Validation: **61 images**
- Testing: **62 images**

## 🗂️ Dataset

The project uses a banana leaf image dataset containing **408 images across 7 classes**.

The dataset was used only for model development and evaluation and is **not included in this repository**.

### Classes

- Banana Healthy Leaf
- Banana Insect Pest Disease
- Banana Black Sigatoka Disease
- Banana Moko Disease
- Banana Bract Mosaic Virus Disease
- Banana Panama Disease
- Banana Yellow Sigatoka Disease

## 🧠 Models Used

### 1. HOG + SVM

Histogram of Oriented Gradients (HOG) was used to extract shape and edge information from the leaf images.

The extracted features were then classified using a Support Vector Machine (SVM).

This approach was used as a classical machine learning baseline.

### 2. MobileNetV2

MobileNetV2 was used as a lightweight deep learning model through transfer learning.

The approach was selected because the dataset is relatively small. Class weights were also used during training to reduce the effect of class imbalance.

## 📈 Evaluation Metrics

The models were evaluated using:

- Accuracy
- Precision
- Recall
- F1-score
- Macro F1-score
- Confusion Matrix

Macro F1-score was considered particularly useful because the dataset is imbalanced.

## 🏆 Results

| Model | Test Accuracy | Macro F1 |
|---|---:|---:|
| HOG + SVM | 50.00% | 0.32 |
| MobileNetV2 | **90.32%** | **0.87** |

MobileNetV2 significantly outperformed the HOG + SVM baseline.

This indicates that the learned visual features from MobileNetV2 were more effective than handcrafted HOG features for distinguishing the disease classes in this dataset.

## 🔍 Example Prediction

A test image belonging to the **Banana Bract Mosaic Virus Disease** class was correctly classified by MobileNetV2 with a confidence of **84.49%**.

## ⚠️ Limitations

- The dataset contains only 408 images.
- The class distribution is imbalanced.
- The smallest class contains only 23 images.
- The test set contains only 3 images for Banana Yellow Sigatoka Disease.
- Differences in lighting, background, leaf orientation, and image quality may affect performance.
- The MobileNetV2 model showed some indication of overfitting.

## 🔄 Project Pipeline

```text
Dataset
   ↓
Data Inspection
   ↓
Preprocessing
   ↓
Stratified Split
   ↓
 ┌───────────────┬──────────────────┐
 │ HOG + SVM     │ MobileNetV2      │
 └───────────────┴──────────────────┘
          ↓
    Model Evaluation
          ↓
    Model Comparison
          ↓
   Example Prediction


