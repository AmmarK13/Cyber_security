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
- **Type:** Random Forest classifier
- **Input:** 18 Features


**Baseline Architecture Example:**


---

## Training & Evaluation
- **Train-Test Split:** Stratified 80-20
- **Metrics Monitored:**
  - Precision
  - Recall
  - F1 score
- **Performance:**  
  Near-perfect scores on validation data:
  - F1 score ≈ 0.98
  - Precision ≈ 0.96 
  - Recall ≈ 0.98 

---

## Usage
1. Clone the repository:
```bash
git clone <repo-url>
cd <repo-folder>

pip install -r requirments.txt

# preprocessing.ipynb
# model_training.ipynb

