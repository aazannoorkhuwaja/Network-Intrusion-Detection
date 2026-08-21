# 🛡️ Network Intrusion Detection System (NIDS)

![Python](https://img.shields.io/badge/Python-3.8%2B-blue.svg?style=for-the-badge&logo=python&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange.svg?style=for-the-badge&logo=jupyter&logoColor=white)
![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-F7931E.svg?style=for-the-badge&logo=scikit-learn&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458.svg?style=for-the-badge&logo=pandas&logoColor=white)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen.svg?style=for-the-badge)

An intelligent, multi-tiered **Network Intrusion Detection System** that analyzes network connection records to classify traffic as either **Normal (0)** or an **Attack (1)** using classical AI heuristics, supervised machine learning, unsupervised clustering, and evolutionary algorithms.

---

## 👥 Authors & Project Info

* **Course:** Artificial Intelligence — Semester Project
* **Group Members:**
  * **Azaan Noor Khuwaja** *(Roll # 24P-0706)* — EDA, Reflex Agent, Supervised Learning (Tasks 1, 2, 3)
  * **M. Uzair Shoaib** *(Roll # 24P-0507)* — Custom K-Means, PCA Visualizations, Genetic Algorithm (Tasks 4, 5)

---

## 📌 Project Overview & Tasks

The project evaluates 6,000 balanced connection records (3,000 normal, 3,000 attack) across 15 numeric traffic features. The implementation covers 5 sequential tasks:

1. **Task 1 — Data Exploration (EDA):** Dataset statistics (`df.describe()`), class distribution bar plot, and feature histograms (`src_bytes`, `count`, `serror_rate`).
2. **Task 2 — Simple Reflex Agent:** Baseline rule-based agent using handcrafted condition-action thresholds (**86.00% accuracy**).
3. **Task 3 — Supervised Machine Learning:** Evaluated on an 80/20 stratified split (`StandardScaler` normalization):
   * **K-Nearest Neighbors (KNN):** Best performance at $k=1$ (**95.58% accuracy**).
   * **Gaussian Naïve Bayes:** Probabilistic baseline (**78.75% accuracy**).
   * **Logistic Regression:** Linear classifier (**91.83% accuracy**).
4. **Task 4 — Unsupervised K-Means Clustering:** Implemented from scratch in plain Python ($K=2$, **~86.60% accuracy**) paired with 2D PCA scatter plots.
5. **Task 5 — Genetic Algorithm Feature Selection:** Plain Python binary GA (Roulette Wheel selection, single-point crossover, bit-flip mutation) to select an optimal 10-feature subset (**91.50% accuracy**).

---

## 📊 Benchmark Results Summary

| Model / Method | Category | Accuracy | Precision | Recall | F1-Score | Key Takeaway |
|---|---|:---:|:---:|:---:|:---:|---|
| **Simple Reflex Agent** | Rule-Based Heuristic | 86.00% | 0.8241 | 0.9160 | 0.8676 | Effective baseline; static thresholds can be bypassed. |
| **Gaussian Naïve Bayes** | Supervised | 78.75% | 0.9320 | 0.6167 | 0.7420 | Suboptimal due to feature independence assumption violations. |
| **Logistic Regression (All Features)** | Supervised | 91.83% | 0.9022 | 0.9383 | 0.9199 | Strong linear benchmark; highly interpretable. |
| **K-Means Clustering ($K=2$)** | Unsupervised | ~86.60% | — | — | — | Strong natural grouping without seeing labels. |
| **GA + Logistic Regression (10 Features)** | Evolutionary Optimization | 91.50% | 0.8992 | 0.9350 | 0.9167 | 33% feature reduction with only 0.33% loss in accuracy. |
| **K-Nearest Neighbors ($k=1$)** | Supervised | **95.58%** | **0.9458** | **0.9667** | **0.9563** | **Top Performer**; captures complex non-linear boundaries. |

---

## 📁 Repository Structure

```text
Network-Intrusion-Detection/
│
├── AI_Final_Project.ipynb       # Main Jupyter notebook containing code for Tasks 1–5
├── Final_Report_Project.pdf     # 9-page comprehensive project report (PDF format)
├── project_statement.txt        # Official project assignment statement & guidelines
├── README.md                    # Project documentation and step-by-step setup guide
├── .gitignore                   # Git configuration rules
└── dataset/                     # Local dataset directory
    └── network_traffic.csv      # Cleaned network connection dataset (6,000 records)
```

---

## 🚀 Step-by-Step Setup & Testing Guide (Zero to Running)

Follow these easy steps to get the environment configured and run the project from scratch.

### Step 1 — Prerequisites Check
Ensure you have **Python 3.8 or higher** installed. You can check your Python version by opening a terminal and running:

```bash
python3 --version   # Linux / macOS
python --version    # Windows
```

---

### Step 2 — Clone the Repository

Clone this repository to your local machine using Git:

```bash
git clone https://github.com/aazannoorkhuwaja/Network-Intrusion-Detection.git
cd Network-Intrusion-Detection
```

---

### Step 3 — Create & Activate a Virtual Environment

Creating a virtual environment ensures clean, isolated dependencies.

* **Linux / macOS:**
  ```bash
  python3 -m venv venv
  source venv/bin/activate
  ```

* **Windows (Command Prompt):**
  ```cmd
  python -m venv venv
  venv\Scripts\activate
  ```

* **Windows (PowerShell):**
  ```powershell
  python -m venv venv
  .\venv\Scripts\Activate.ps1
  ```

---

### Step 4 — Install Required Dependencies

Install Jupyter and all essential data science & ML libraries in one command:

```bash
pip install notebook numpy pandas matplotlib scikit-learn
```

---

### Step 5 — Verify Dataset Location

Ensure the dataset file is placed in the `dataset/` subfolder at the root of the repository:

```text
Network-Intrusion-Detection/
└── dataset/
    └── network_traffic.csv
```

---

### Step 6 — Launch & Test the Notebook

1. **Launch Jupyter Notebook:**
   ```bash
   jupyter notebook
   ```
   *(This will automatically open your default browser at `http://localhost:8888`)*

2. **Open the Notebook:**
   In the Jupyter file navigator, click on **`AI_Final_Project.ipynb`**.

3. **Run & Test Everything:**
   * **Automated Run:** Go to the top menu and select **`Kernel → Restart & Run All`**. This will execute all cells sequentially from Task 1 through Task 5.
   * **Step-by-Step Execution:** Click on the first cell and press **`Shift + Enter`** to execute cell-by-cell.

4. **Verify Output:**
   * Plots (histograms, bar charts, PCA scatter plots) will display directly beneath the code cells.
   * Evaluation tables and metrics (Accuracy, Confusion Matrices, Precision, Recall, F1) will print cleanly in the output cells.

---

## 🛠️ Troubleshooting

| Issue | Cause | Easy Solution |
|---|---|---|
| `jupyter: command not found` | Jupyter is not installed in the active environment | Run `pip install notebook` |
| `ModuleNotFoundError: No module named 'pandas'` | Missing Python libraries | Run `pip install numpy pandas matplotlib scikit-learn` |
| `FileNotFoundError: dataset/network_traffic.csv` | Dataset missing or mislocated | Ensure `network_traffic.csv` is inside the `dataset/` directory |
| Port 8888 already in use | Another Jupyter instance is running | Run `jupyter notebook --port 8889` |
| Execution permissions (Windows PowerShell) | Script execution policy disabled | Run `Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass` |

---

## 📄 License & Acknowledgments

Developed as part of the Artificial Intelligence Course (Fast University). All data, code, and PDF report assets are available under standard open project academic usage.
