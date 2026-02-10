# Brute-Force Attack Detection using Neural Networks

## Project Overview
This project implements a neural network-based Intrusion Detection System (IDS) specialized for **brute-force attacks**. The model is trained on the **CIC-IDS 2018 dataset (02-14-2018 subset)** and identifies brute-force attack patterns with high accuracy.

The primary goal is to explore deep learning approaches for network security and build a baseline IDS for brute-force detection.

---

## Dataset
- **Source:** [CIC-IDS 2018](https://www.unb.ca/cic/datasets/ids-2018.html)
- **Subset Used:** February 14, 2018
- **Classes:**  
  - `Benign`  
  - `Brute-force attacks` (SSH, FTP)
- **Number of Features:** 64 numeric features after preprocessing
- **Preprocessing Steps:**
  - Removed NaNs and infinite values
  - Replaced negative values where appropriate (`-1` → `0` in window size columns)
  - Removed duplicates selectively
  - Removed zero-variance columns
  - Combined SSH and FTP brute-force attacks into one class
  - Scaled numeric features using **StandardScaler**
  - Encoded categorical features (`Protocol` via one-hot encoding, `Dst_Port` bucketed and one-hot encoded)

---

## Model Architecture
- **Type:** Fully-connected feedforward neural network (MLP)
- **Input:** 70 features
- **Hidden Layers:** 3 layers with ReLU activations, optional Dropout for regularization
- **Output:** 1 neuron with Sigmoid activation (binary classification)
- **Loss Function:** `BCEWithLogitsLoss`
- **Optimizer:** Adam
- **Training Parameters:**
  - Epochs: 30
  - Batch size: 1024
  - Learning rate: 1e-3

**Baseline Architecture Example:**


---

## Training & Evaluation
- **Train-Test Split:** Stratified 80-20
- **Metrics Monitored:**
  - Training and validation loss
  - ROC-AUC
  - Precision
  - Recall
- **Performance:**  
  Near-perfect scores on validation data:
  - ROC-AUC ≈ 1.0  
  - Precision ≈ 1.0  
  - Recall ≈ 1.0  

> **Note:** Perfect performance is likely due to dataset simplicity and clear separability between benign and brute-force attack patterns.

---

## Usage
1. Clone the repository:
```bash
git clone <repo-url>
cd <repo-folder>

pip install -r requirments.txt

# preprocessing.ipynb
# model_training.ipynb

