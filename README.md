# 🫀 AI-Assisted Detection of Myocardial Infarction, Abnormal Heartbeat & Normal ECG

This repository presents my research work on developing an **AI-assisted diagnostic system** for detecting **Myocardial Infarction (Heart Attack)**, **Abnormal Heartbeat**, and **Normal** cases from **ECG (Electrocardiogram) images** using **Deep Learning**.  
The model utilizes a **fine-tuned ResNet50** architecture enhanced with an **Adaptive Categorical Focal Loss** function to address class imbalance and improve diagnostic robustness.

---

## 🎯 Project Overview

Electrocardiography (ECG) remains one of the most widely used and cost-effective diagnostic tools for identifying cardiovascular diseases.  
However, manual ECG interpretation is **time-consuming**, **error-prone**, and highly dependent on clinician expertise, particularly in **resource-limited healthcare environments**.

To support clinical decision-making, I developed an **AI-powered Computer-Aided Diagnostic (CAD)** system capable of classifying ECG images into:

- **Normal**
- **Abnormal Heartbeat**
- **Myocardial Infarction (MI)**

This research lies within the domain of **AI for Cardiology** and **Medical Image Analysis (MIA)**, helping advance early detection of life-threatening cardiac conditions.

---

## 🧩 Dataset

The dataset used in this study is publicly available on Kaggle:

📌 **Dataset Source:**  
ECG Heartbeat Classification Image Dataset  
🔗 https://www.kaggle.com/datasets/evilspirit05/ecg-analysis

| Class | Description |
|-------|-------------|
| **Normal** | ECG of individuals without cardiac irregularities |
| **Abnormal Heartbeat** | Irregular ECG pattern (non-MI) |
| **Myocardial Infarction (MI)** | ECG of patients with heart attack |

### Data Split:
- **70% Training**
- **15% Validation**
- **15% Testing**

---

## 🧠 Model Architecture

**Base Model:** ResNet50 (pretrained on ImageNet)

Training was conducted in two phases:

1️⃣ **Feature Extraction Phase**  
   - The ResNet50 base was frozen to leverage general visual features.

2️⃣ **Fine-Tuning Phase**  
   - The final **20 layers** of ResNet50 were unfrozen.
   - This allowed learning of domain-specific ECG waveform patterns.


---

## ⚙️ Adaptive Categorical Focal Loss (Research Contribution)

To overcome class imbalance, especially the relatively lower availability of genuine MI cases, I incorporated a **custom adaptive focal loss**.  
It dynamically updates **α (alpha)** and **γ (gamma)** based on class-wise recall at each epoch.

\[
FL(p_t) = - \alpha_t (1 - p_t)^{\gamma_t} \log(p_t)
\]

### Why Adaptive Loss?
- Traditional focal loss uses fixed α and γ.
- Here, both parameters **self-adjust** to penalize classes with poor recall.
- Creates a **feedback loop** that balances sensitivity across all classes.

> ⚠ Implementation details of the adaptive update mechanism are part of ongoing research and may be published in a future manuscript. Source code is available upon request.

---

## 🚀 Training Configuration

| Setting | Value |
|--------|-------|
| Optimizer | Adam |
| Initial Learning Rate | 0.001 (reduced on plateau) |
| Batch Size | 32 |
| EarlyStopping | Patience = 3 (restore best weights) |
| ModelCheckpoint | Saves best model on validation loss |
| Fine-Tuning | Last 20 ResNet layers unfrozen |

---

## 📊 Results

The model achieved strong performance during testing:

Classification Report:
                        precision    recall  f1-score   support

               Normal       1.00      1.00      1.00       284
     Heart arrhythmia       1.00      1.00      1.00       233
Myocardial Infarction       1.00      1.00      1.00       239

             accuracy                           1.00       756
            macro avg       1.00      1.00      1.00       756
         weighted avg       1.00      1.00      1.00       756

> Actual results may vary based on training runs and hardware.

---

## 🔬 Interpretability (Future Work)

The model architecture supports medical explainability techniques such as:

- **Grad-CAM / Grad-CAM++**
- **Integrated Gradients**
- **Score-CAM**

These can reveal which waveform regions influenced diagnostic decisions — beneficial for clinical validation.

---

## 🧰 Tech Stack

| Tool | Purpose |
|------|--------|
| TensorFlow / Keras | Deep learning training |
| scikit-learn | Model evaluation metrics |
| NumPy, Pandas | Data preprocessing |
| Matplotlib / Seaborn | Visualization |
| Kaggle | Dataset source & experiments |

---


---

## 🎓 Research Significance

This project demonstrates that **transfer learning combined with adaptive loss optimization** can effectively support clinical ECG screening systems, especially where cardiology experts are limited.

It contributes toward:

- Early detection of **life-threatening cardiac conditions**
- Reducing diagnostic workload for healthcare professionals
- Expanding **AI-driven cardiology** research

---

## 👨‍💻 Author

**Hamza Shahid**  
Bachelor of Biomedical Engineering (with Distinction)  
University of Engineering & Technology (UET), Lahore

🔍 Research Interests:  
AI in Healthcare • Medical Image Analysis • Cardiovascular AI • Deep Neural Networks

---

## 📜 License

Released under the **MIT License** — free to use for academic and research purposes.

---

## 🌍 Acknowledgment

Thanks to the open-source medical AI community and Kaggle contributors supporting transparent and accessible healthcare innovation.


