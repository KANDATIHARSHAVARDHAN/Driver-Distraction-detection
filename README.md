# 🚗 Driver Distraction Detection using CNN

This repository contains a **Convolutional Neural Network (CNN)** for detecting driver distractions from images. The model classifies 10 different driver behaviors using the **State Farm Distracted Driver Dataset**.

---

## 🔹 Features

- Preprocessing and augmentation of driver images
- Custom CNN architecture with parallel branches
- Training with class balancing
- Model evaluation: accuracy, loss, confusion matrix
- Save and load trained model

---

## 🖼️ Dataset Description

The dataset contains images of drivers categorized into **10 classes**:

| Class | Behavior                       |
|-------|--------------------------------|
| c0    | Normal driving                 |
| c1    | Texting - right                |
| c2    | Talking on the phone - right   |
| c3    | Texting - left                 |
| c4    | Talking on the phone - left    |
| c5    | Operating the radio            |
| c6    | Drinking                       |
| c7    | Reaching behind                |
| c8    | Hair and makeup                |
| c9    | Talking to passenger           |

---

## 🏗️ CNN Architecture
```bash
                              ┌───────────────────────────────┐
                              │       Input (224x224x3)       │
                              └───────────────┬───────────────┘
                                              ▼
                              ┌───────────────────────────────┐
                              │  Conv2D 128 filters (3x3)      │
                              │       ReLU Activation          │
                              └───────────────┬───────────────┘
                                              ▼
                              ┌───────────────────────────────┐
                              │  Conv2D 128 filters (3x3)      │
                              │       ReLU Activation          │
                              └───────────────┬───────────────┘
                                              ▼
                              ┌───────────────────────────────┐
                              │        MaxPooling2D (2x2)      │
                              └───────────────┬───────────────┘
                                              ▼
                              ┌───────────────────────────────┐
                              │  Conv2D 256 filters (3x3)      │
                              │       ReLU Activation          │
                              └───────────────┬───────────────┘
                                              ▼
                              ┌───────────────────────────────┐
                              │  Conv2D 256 filters (3x3)      │
                              │       ReLU Activation          │
                              └───────────────┬───────────────┘
                                              ▼
                              ┌───────────────────────────────┐
                              │        MaxPooling2D (2x2)      │
                              └───────────────┬───────────────┘
                                              ▼
                              ┌───────────────────────────────┐
                              │        Parallel Branches       │
                              └───────────────┬───────────────┘
                                              ▼
              ┌───────────────────────────────┐       ┌───────────────────────────────┐
              │           Branch 1           │       │           Branch 2           │
              │       Conv2D 64 filters      │       │       Conv2D 64 filters      │
              │       Conv2D 64 filters      │       │       Conv2D 64 filters      │
              └───────────────┬──────────────┘       └───────────────┬──────────────┘
                              ▼                                   ▼
                              └───────────────┬───────────────────┘
                                              ▼
                              ┌───────────────────────────────┐
                              │         Concatenate            │
                              └───────────────┬───────────────┘
                                              ▼
                              ┌───────────────────────────────┐
                              │            Flatten             │
                              └───────────────┬───────────────┘
                                              ▼
                              ┌───────────────────────────────┐
                              │          Dense 64 (ReLU)       │
                              └───────────────┬───────────────┘
                                              ▼
                              ┌───────────────────────────────┐
                              │        Dense 10 (Softmax)      │
                              └───────────────┬───────────────┘
                                              ▼
                              ┌───────────────────────────────┐
                              │         Output 10 Classes      │
                              └───────────────────────────────┘
```

---

## ⚙️ Setup Instructions

Install dependencies:

```bash
pip install tensorflow keras scikit-learn matplotlib seaborn numpy pandas tqdm
```





