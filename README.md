# [data set link](https://www.physionet.org/content/sleep-edfx/1.0.0/ )

# 💤 Sleep Cycle Analysis Project

## 📌 Project Overview
This project aims to develop an AI model for predicting sleep cycles using the **Sleep-EDF dataset**. We analyze various factors such as **sleep duration, EEG signals, and sleep stages (REM, NREM, etc.)** to assess their impact on sleep quality. By leveraging **machine learning and deep learning models**, we explore the best approach for accurate sleep stage classification.

## 👥 Team Members & Roles
- **Alexis Blackwell** - Data Preprocessing 📊
- **Elizabeth Bui** - Documentation 📝
- **Sai Charan Merugu** - Model Testing & Validation 🤖

## 📂 Dataset Information
We utilize the **PhysioNet Sleep Database**, which includes **197 full-night polysomnographic recordings** with:
- **EEG (Electroencephalography)** - Measures brain activity
- **EMG (Electromyography)** - Measures muscle activity
- **EOG (Electrooculogram)** - Measures eye movement
- **Polysomnography (PSG)** - Combines EEG, EMG, and EOG for sleep disorder diagnosis

## 💤 Sleep Stages & EEG Patterns
| **Stage**  | **Description** | **EEG Patterns** |
|------------|---------------|------------------|
| **Wake** | Awake or drowsy | Beta waves (fully awake), Alpha waves (drowsy) |
| **REM** | Dreaming sleep | Beta waves |
| **NREM 1** | Light sleep | Theta waves |
| **NREM 2** | Deeper sleep | Delta waves |
| **NREM 3** | Deepest sleep | Delta waves (low frequency, high amplitude) |

## 🛠️ Preprocessing & Challenges
### 🚧 Challenges
- **Memory Issues**: The raw dataset (each file ~8.5 million rows) was too large for direct processing.
- **Class Imbalance**: Wakefulness (Stage 0) dominated, making the model biased.

### 🔧 Solutions
- **Random Sampling**: Selected 10 patient samples to reduce memory usage.
- **Proportionate Stratified Sampling**: Ensured balanced representation of sleep stages.

## 📈 Feature Selection
| Feature | Type | Importance |
|---------|------|------------|
| **Fpz-Cz** | EEG | Strong correlation with sleep class |
| **Pz-Oz** | EEG | Strong correlation with sleep class |
| **Submental_binned** | EMG | Weak correlation, excluded from model |

## 🤖 Machine Learning Models & Results
We tested multiple models, optimizing them with **hyperparameter tuning (HPT)**:

### 🌳 Random Forest Classifier
- **Baseline Accuracy**: Moderate
- **HPT Accuracy**: **69%**
- **Strengths**: High recall for **Stage 4 (Deep Sleep)** & **Stage 6 (Movement Time)**
- **Weaknesses**: Struggled with **Stage 1 (Light Sleep)** & **Stage 5 (REM Sleep)**

### 🌲 Decision Tree
- **Baseline Accuracy**: **38%** (low, potential underfitting)
- **HPT Accuracy**: **64%**
- **Strengths**: High precision for **Stage 6**
- **Weaknesses**: Poor performance on **Stage 1 & Stage 5**

### 🔥 XGBoost
- **Baseline Accuracy**: **64.7%**
- **HPT Accuracy**: **64.7%**
- **Strengths**: High precision & recall for **Stage 5 (REM Sleep)**
- **Weaknesses**: Misclassifications in **Stage 0 & Stage 2**

## 📊 Model Evaluation Metrics
| Model | Precision | Recall | F1 Score |
|-------|-----------|--------|---------|
| **Random Forest (HPT)** | High | Low | Low |
| **Decision Tree (HPT)** | Moderate | Moderate | Moderate |
| **XGBoost (HPT)** | High | High | High |

## 🔮 Future Work
- **Process more patient data**: Scale from **10 → 20 → 50 patients**.
- **Test advanced models**: LSTMs, CNN-LSTMs, K-means clustering.
- **Improve class balance**: Use **undersampling** or **oversampling** techniques.

## 📚 References & Related Work
1. **Deep Learning Model for Sleep Stage Prediction**  
   - **Journal of Sleep Research** (85.2% accuracy using Attention Bi-LSTM)  
   - [🔗 Read More](https://doi.org/10.1111/jsr.14050)

2. **AI-Driven Sleep Staging with Wearables**  
   - **PLOS ONE** (79% accuracy using SLAMSS)  
   - [🔗 Read More](https://doi.org/10.1371/journal.pone.0285703)

## 📎 Resources & Tools
- **Libraries**: `scikit-learn`, `TensorFlow`, `PyTorch`, `MNE`, `Pyedflib`
- **Dataset**: Sleep-EDF Dataset from **PhysioNet**
- **Feature Engineering**: EEG signal processing, statistical & frequency domain features



🚀 **Let's improve sleep science with AI!** 💤

