# 🛡️ Network Intrusion Detection System (NIDS)

![Python](https://img.shields.io/badge/Python-3.8%2B-blue.svg)
![Scikit-Learn](https://img.shields.io/badge/Library-Scikit--Learn-orange.svg)
![Pandas](https://img.shields.io/badge/Library-Pandas-150458.svg)
![NumPy](https://img.shields.io/badge/Library-NumPy-013243.svg)
![Matplotlib](https://img.shields.io/badge/Library-Matplotlib-11557c.svg)
![Jupyter](https://img.shields.io/badge/Interface-Jupyter%20Notebook-orange.svg)
![Status](https://img.shields.io/badge/Project%20Status-Completed-brightgreen.svg)

An intelligent, multi-tiered **Network Intrusion Detection System (NIDS)** built using classical AI algorithms and machine learning techniques. The system classifies network connection records as either **Normal** (0) or **Attack** (1) by leveraging rule-based reflex agents, supervised models, unsupervised clustering, and evolutionary feature selection.

---

## 📑 Table of Contents

- [Overview](#-overview)
- [Key Features](#-key-features)
- [Dataset Specifications](#-dataset-specifications)
- [Experimental Results](#-experimental-results)
- [Project Architecture](#-project-architecture)
- [Installation & Setup](#-installation--setup)
- [Usage Instructions](#-usage-instructions)
- [Troubleshooting](#-troubleshooting)
- [Authors & Acknowledgments](#-authors--acknowledgments)

---

## 🌟 Overview

Network administrators monitor thousands of packet connection logs per minute. Manual inspection is infeasible, requiring automated threat detection systems. This project designs, evaluates, and benchmarks multiple artificial intelligence approaches—ranging from simple heuristic condition-action rules to complex non-linear classification and genetic feature optimization.

---

## 🚀 Key Features

* **Task 1 — Exploratory Data Analysis (EDA):** Class distribution bar charts, summary statistics (`df.describe()`), and per-class overlay histograms (`src_bytes`, `count`, `serror_rate`).
* **Task 2 — Simple Reflex Agent:** Baseline rule-based classifier using handcrafted condition-action thresholds without internal state.
* **Task 3 — Supervised Machine Learning:** Evaluated on a 80/20 stratified split with standardized feature scaling:
  * **K-Nearest Neighbors (KNN):** Hyperparameter sweep $k \in \{1, 3, 5, 7, 9, 11\}$ (Top accuracy at $k=1$).
  * **Gaussian Naïve Bayes:** Probabilistic classifier evaluation.
  * **Logistic Regression:** Linear decision boundary model.
* **Task 4 — Unsupervised K-Means Clustering:** Custom implementation from scratch in plain Python ($K=2$) paired with 2D Principal Component Analysis (PCA) scatter visualizations.
* **Task 5 — Genetic Algorithm (GA) Feature Selection:** Plain Python binary GA (Roulette Wheel selection, single-point crossover, bit-flip mutation) to identify optimal compact feature subsets.

---

## 📊 Dataset Specifications

* **Total Records:** 6,000 connection logs
* **Class Distribution:** Perfectly balanced (3,000 Normal / 3,000 Attack)
* **Feature Dimensions:** 15 numeric traffic attributes (`duration`, `src_bytes`, `dst_bytes`, `serror_rate`, `same_srv_rate`, `count`, etc.)
* **Target Label:** Binary (`0` = Normal Traffic, `1` = Cyber Attack)

> 📌 **Note:** The dataset requires no categorical one-hot encoding or missing value imputation.

---

## 📈 Experimental Results

| Model / Strategy | Type | Accuracy | Precision | Recall | F1-Score | Key Observation |
|---|---|:---:|:---:|:---:|:---:|---|
| **Simple Reflex Agent** | Rule-Based Heuristic | 86.00% | 0.8241 | 0.9160 | 0.8676 | Effective baseline; static thresholds can be bypassed. |
| **Gaussian Naïve Bayes** | Supervised (Probabilistic) | 78.75% | 0.9320 | 0.6167 | 0.7420 | Suboptimal due to feature independence assumption violations. |
| **Logistic Regression (All Features)** | Supervised (Linear) | 91.83% | 0.9022 | 0.9383 | 0.9199 | Highly interpretable, strong performance. |
| **K-Means Clustering ($K=2$)** | Unsupervised | ~86.60% | — | — | — | Strong structural grouping without seeing ground-truth labels. |
| **GA + Logistic Regression (10 Features)** | Evolutionary Optimization | 91.50% | 0.8992 | 0.9350 | 0.9167 | Reduced feature set by 33% with minimal (0.33%) accuracy loss. |
| **K-Nearest Neighbors ($k=1$)** | Supervised (Non-Linear) | **95.58%** | **0.9458** | **0.9667** | **0.9563** | **Highest Performing Model**; captures complex decision boundaries. |

---

## 📁 Project Architecture

```text
Network-Intrusion-Detection/
│
├── AI_Final_Project.ipynb       # Main Jupyter notebook containing implementation for Tasks 1–5
├── Final_Report_Project.pdf     # 9-page comprehensive project report (PDF format)
├── README.md                    # Project documentation & execution guide
├── .gitignore                   # Git exclusion rules
└── dataset/                     # Local dataset directory
    └── network_traffic.csv      # Cleaned network connection records (6,000 rows)
```

---

## 💻 Installation & Setup

### Prerequisites

* **Python 3.8+** installed.
* **Jupyter Notebook** or **JupyterLab**.

### 1. Clone the Repository

```bash
git clone https://github.com/aazannoorkhuwaja/Network-Intrusion-Detection.git
cd Network-Intrusion-Detection
```

### 2. Create a Virtual Environment (Optional but Recommended)

* **Linux / macOS:**
  ```bash
  python3 -m venv venv
  source venv/bin/activate
  ```

* **Windows:**
  ```cmd
  python -m venv venv
  venv\Scripts\activate
  ```

### 3. Install Required Dependencies

```bash
pip install notebook numpy pandas matplotlib scikit-learn
```

---

## 🕹️ Usage Instructions

1. Launch Jupyter Notebook in your terminal:
   ```bash
   jupyter notebook
   ```
2. Open **`AI_Final_Project.ipynb`** from the Jupyter web dashboard (`http://localhost:8888`).
3. To run the full pipeline from data exploration to the Genetic Algorithm, select from the top menu:
   ```text
   Kernel → Restart & Run All
   ```

---

## 🔧 Troubleshooting

| Common Issue | Solution |
|---|---|
| `jupyter: command not found` | Run `pip install notebook` inside your active environment. |
| `ModuleNotFoundError: No module named 'pandas'` | Execute `pip install pandas numpy matplotlib scikit-learn`. |
| `FileNotFoundError: dataset/network_traffic.csv` | Ensure the `dataset` folder containing `network_traffic.csv` is in the repository root directory. |
| Port 8888 occupied | Launch Jupyter on an alternate port: `jupyter notebook --port 8889`. |

---

## 👥 Authors & Acknowledgments

* **Azaan Noor Khuwaja** — *(Roll # 24P-0706)* — EDA, Reflex Agent, Supervised Classifiers (Tasks 1, 2, 3)
* **M. Uzair Shoaib** — *(Roll # 24P-0507)* — Custom K-Means, PCA Visualizations, Genetic Algorithm (Tasks 4, 5)

*Developed for the Artificial Intelligence Semester Project.*
