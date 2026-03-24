# 🧠 AI-Based Stutter Detection & Classification using Speech Biomarkers

## 📌 Overview

This project presents a deep learning-based system for analyzing speech to detect stuttering and classify different types of dysfluencies. The system leverages audio signal processing and sequence modeling to understand temporal speech patterns.

A two-stage architecture is implemented:
1. **Stutter Detection (Binary Classification)**
2. **Stutter Type Classification (Multi-label Classification)**

---

## 🎯 Objectives

- Detect whether a speech sample contains stuttering  
- Classify different stutter types in speech  
- Build an end-to-end pipeline using audio features  

---

## 📂 Dataset

- **UCLASS Stuttered Speech Dataset (SEP-28k format)**
- ~4700 audio clips (3 seconds each)
- Multi-label annotations:
  - Block  
  - Prolongation  
  - Sound Repetition  
  - Word Repetition  
  - Interjection  

### 📊 Data Insights

- ~2490 stutter samples  
- ~2220 fluent samples  
- Nearly balanced dataset for binary classification  

To improve model stability, the following classes were selected for multi-label classification:
- **Block**
- **Sound Repetition**
- **Interjection**

---

## ⚙️ Methodology

### 🎧 Feature Extraction

- Extracted **MFCC (Mel Frequency Cepstral Coefficients)** from audio  
- Captures speech characteristics like:
  - Frequency patterns  
  - Tone and articulation  
- All sequences were padded to fixed length for LSTM input  

---

## 🧠 Model Architecture

### 🔹 Model 1: Stutter Detection

- Input: MFCC sequences  
- Architecture:
  - LSTM (64 units)
  - LSTM (32 units)
  - Dropout layers
  - Dense layers
- Output:
  - `0 → Fluent`
  - `1 → Stutter`

### ✅ Performance:
- **Accuracy: ~88.6%**

---

### 🔹 Model 2: Stutter Type Classification

- Input: MFCC (only stutter samples)
- Output (multi-label):
  - `[Block, SoundRep, Interjection]`
- Activation: Sigmoid  
- Loss: Binary Crossentropy  

### ✅ Performance:
- **Accuracy: ~63.6%**
- **F1-score (micro avg): ~0.71**

---

## 📊 Results & Insights

### 🔹 Binary Classification
- Strong performance (~89% accuracy)
- Balanced dataset enabled stable learning

---

### 🔹 Multi-label Classification

| Class          | F1 Score | Observation                  |
|----------------|----------|------------------------------|
| Block          | ~0.77    | Strong performance           |
| SoundRep       | ~0.76    | Most dominant class          |
| Interjection   | ~0.50    | Lower due to fewer samples   |

### 🧠 Key Observations

- Multi-label classification is significantly more challenging than binary classification  
- Class imbalance impacts performance of less frequent dysfluency types  
- Model successfully captures overlapping stutter patterns  

---

## 📉 Training Behavior

- Training loss decreased steadily  
- Validation loss showed mild fluctuations  
- Indicates:
  - Stable learning  
  - Controlled overfitting (via Dropout & EarlyStopping)  

---

## ⚠️ Limitations

- Limited dataset size (~4700 samples)  
- Class imbalance across stutter types  
- Lack of real-world noisy audio conditions  
- Multi-label complexity reduces performance  

---

## 🚀 Future Improvements

- Use larger datasets (e.g., full SEP-28k)  
- Apply pretrained models (e.g., wav2vec, HuBERT)  
- Include additional speech biomarkers:
  - Pitch  
  - Energy  
- Real-time speech analysis system  
- Class imbalance handling using weighted loss  

---

## 🧠 Tech Stack

- Python  
- Librosa  
- NumPy, Pandas  
- TensorFlow / Keras  
- Scikit-learn  

---

## 💡 Conclusion

This project demonstrates how speech biomarkers can be used to detect and analyze stuttering patterns using deep learning. The two-stage architecture improves interpretability by separating detection and classification tasks.

The results highlight both the potential and challenges of modeling real-world speech disorders using AI.

---

## ⭐ If you found this useful, consider giving a star!
