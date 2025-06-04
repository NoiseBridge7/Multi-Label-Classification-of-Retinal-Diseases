# 🧠 Multi-Label Classification of Retinal Diseases

This project applies deep learning techniques to perform **multi-label classification** on retinal fundus images from the [ODIR-5K dataset](https://www.kaggle.com/datasets/andrewmvd/ocular-disease-recognition-odir5k). The goal is to identify multiple co-existing ocular diseases in a single image using a VGG19-based model enhanced with class imbalance handling via SMOTE.

---

## 📁 Project Structure

```plaintext
├── Multi-Label Classification of Retinal Diseases.ipynb
├── README.md
├── /data
│   └── (ODIR-5K dataset - not uploaded due to size)
```

---

## 🧾 Table of Contents

- [About the Project](#about-the-project)
- [Dataset](#dataset)
- [Methodology](#methodology)
- [Model Architecture](#model-architecture)
- [Evaluation Metrics](#evaluation-metrics)
- [Results](#results)
- [How to Run](#how-to-run)
- [Team Members](#team-members)
- [References](#references)

---

## 📌 About the Project

A deep learning-based system that classifies retinal diseases such as:

- Diabetic Retinopathy
- Glaucoma
- Cataract
- Age-related Macular Degeneration (AMD)
- Hypertension
- Myopia
- and more...

This project leverages:

- **VGG19 Transfer Learning**
- **SMOTE for class imbalance**
- **Stratified K-Fold Cross-Validation**

---

## 📊 Dataset

- **Source**: [ODIR-5K Dataset from Kaggle](https://www.kaggle.com/datasets/andrewmvd/ocular-disease-recognition-odir5k)
- **Samples**: 5000 fundus images
- **Labels**: Multi-labels per image (up to 8 disease conditions)

---

## ⚙️ Methodology

1. **Data Preprocessing**

   - Resize images to `224x224`
   - Normalize pixel values
   - Convert clinical annotations to multi-label format

2. **Class Imbalance Handling**

   - Custom SMOTE (up to 500 samples/class)
   - Sampling strategy: `max(original, 30% of max class size, cap=500)`

3. **Model Training**

   - VGG19 with frozen base layers
   - Fine-tuning dense layers with dropout
   - Loss: Binary Cross-Entropy

4. **Validation**
   - 5-Fold Stratified Cross-Validation

---

## 🧱 Model Architecture

- **Base**: VGG19 (pretrained on ImageNet)
- **Modifications**:
  - Global Average Pooling
  - Fully Connected Layers
  - Sigmoid activation for multi-label output

---

## 📈 Evaluation Metrics

- Accuracy
- Precision, Recall, F1-Score (Macro & Weighted)
- Hamming Loss
- Confusion Matrix (per disease label)

---

## 📊 Results

| Metric                | Before SMOTE | After SMOTE |
| --------------------- | ------------ | ----------- |
| Accuracy              | 86%          | 93%         |
| Macro F1-Score        | 0.81         | 0.93        |
| Weighted F1-Score     | 0.83         | 0.93        |
| Recall (Hypertension) | 0.54         | 0.89        |

---

## ▶️ How to Run

1. Open the notebook in [Google Colab](https://colab.research.google.com/).
2. Upload your `kaggle.json` to access the dataset.
   2.1 To get the kaggle.json file if you dont have one it is present in the settings tab of your kaggle account as API
   Note: It is important you have this file as it allows the dataset to be used in collab
3. Run all cells in the notebook `Multi-Label Classification of Retinal Diseases.ipynb`.

> **Note:** You need to download the dataset from [Kaggle](https://www.kaggle.com/datasets/andrewmvd/ocular-disease-recognition-odir5k) manually and follow the instructions inside the notebook to place it correctly.

---

## 👨‍💻 Team Members

- Pavan
- Pratheeth Udupa
- Prajwal V Shet
- Channa Basava

---

## 📚 References

- [ODIR-5K Dataset](https://www.kaggle.com/datasets/andrewmvd/ocular-disease-recognition-odir5k)
- Simonyan & Zisserman (VGG19)
- SMOTE: Chawla et al., 2002
