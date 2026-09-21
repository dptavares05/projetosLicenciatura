# Brain Tumor Diagnosis Prediction — Machine Learning Classification

Supervised machine learning pipeline engineered to classify brain tumors as **Malignant (1)** or **Benign (0)** from demographic data and Apparent Diffusion Coefficient (ADC) MRI texture features. Developed for the Kaggle "Diagnóstico de Tumores Cerebrais" competition, prioritizing the **F1-Score** metric and model generalization across unseen test sets.

Developed as part of the Machine Learning (Aprendizagem Automática) curriculum at the University of Évora.

---

## Tech Stack & Tools

### Platform & Libraries
![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)
![scikit-learn](https://img.shields.io/badge/scikit--learn-%23F7931E.svg?style=for-the-badge&logo=scikit-learn&logoColor=white)
![Pandas](https://img.shields.io/badge/pandas-%23150458.svg?style=for-the-badge&logo=pandas&logoColor=white)
![NumPy](https://img.shields.io/badge/numpy-%23013243.svg?style=for-the-badge&logo=numpy&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-%23F37626.svg?style=for-the-badge&logo=Jupyter&logoColor=white)
![Git](https://img.shields.io/badge/git-%23F05033.svg?style=for-the-badge&logo=git&logoColor=white)

---

## Dataset & Aggregation Strategy

The core technical challenge centered on hierarchical aggregation: predictions are evaluated at the **patient** level, while the raw MRI inputs encompass multiple slice records per subject.

| Feature Category | Features | Preprocessing / Handling Strategy |
| :--- | :--- | :--- |
| **Demographics** | Age, Sex | Encoded and aligned per individual patient identity. |
| **Texture Metrics** | 18 ADC MRI radiomic texture values | Multi-slice variance reduction via mean statistical pooling per patient. |
| **Target Variable** | Diagnosis (`0` = Benign, `1` = Malignant) | Binary classification optimized for class-balanced F1-Score evaluation. |

---

## Model Evaluation & Results

Multiple classification families were tuned to balance model capacity against overfitting risks on a moderate sample size:

| Model Architecture | Strengths & Role in Pipeline | Key Outcome / Generalization |
| :--- | :--- | :--- |
| **Decision Tree** | Interpretable thresholds, non-linear split boundaries | **Best Model**: Achieved peak private test score (**F1 = 0.833**). |
| **Logistic Regression** | Linear baseline, regularized log-odds modeling | Highly stable baseline; prevented variance spikes. |
| **Naive Bayes** | Probabilistic conditional independence baseline | Fast benchmark displaying low sensitivity to noise. |
| **Support Vector Machines (SVM)** | Maximum margin boundary optimization | Solid margin separation across normalized texture spaces. |
| **Random Forest** | Ensemble bagging and feature subsampling | Evaluated against variance reduction vs. single tree simplicity. |

---

## Key Technical Decisions

* **Intra-Patient Aggregation**: Applied statistical mean aggregation across multiple MRI slices per patient, eliminating slice-level noise and stabilizing tabular representation before model ingestion.
* **Overfitting Mitigation**: Given the dataset scale, prioritized controlled model complexities (hyperparameter pruning, depth constraints) to safeguard against public-to-private leaderboard score degradation.
* **Baseline Benchmarking**: Maintained strict evaluation discipline where simpler models (Logistic Regression and Naive Bayes) served as baseline references, preventing artificial inflation of complex ensembles.

---

## Repository Structure

```text
├── notebook_grupoAA.ipynb        # Complete Data Science pipeline (EDA, Preprocessing, Training, Eval)
├── notebook_grupoAA.pdf          # Comprehensive technical report & algorithmic justifications
├── submission_...csv             # Kaggle submission files and scored predictions
└── README.md                     # Project documentation
