# 🔍 Fraud Detection in Government Schemes
### Big Data & Python — College Project

---

## 📌 Project Overview

This project detects fraudulent beneficiaries in government welfare schemes
(PM-KISAN, MGNREGS, PMAY, Ration Card, Scholarship) using **supervised machine
learning** and **big data processing techniques**.

**Key Features:**
- Synthetic dataset of 10,000 beneficiary records with realistic fraud patterns
- Exploratory Data Analysis (EDA) with visualizations
- Feature engineering (derived fraud indicators)
- Three ML models: Logistic Regression, Decision Tree, Random Forest
- Unsupervised anomaly detection via Isolation Forest
- Big Data pipeline: MapReduce aggregation, streaming dedup, rule engine
- Interactive fraud analytics dashboard

---

## 📂 Project Structure

```
fraud_detection_project/
│
├── fraud_detection_main.py     ← Main ML pipeline (run this first)
├── bigdata_pipeline.py         ← Big Data processing module
├── dashboard.py                ← Visual analytics dashboard
├── requirements.txt            ← Python dependencies
├── README.md                   ← This file
│
├── data/                       ← Generated CSV datasets
│   ├── sample_dataset.csv
│   ├── fraud_cases.csv
│   ├── legitimate_cases.csv
│   ├── mapreduce_summary.csv
│   ├── duplicate_ids_flagged.csv
│   ├── high_risk_flagged.csv
│   └── state_partition_analysis.csv
│
└── reports/                    ← Generated plots/charts
    ├── eda_analysis.png
    ├── confusion_matrices.png
    ├── roc_curves.png
    ├── feature_importance.png
    ├── anomaly_detection.png
    ├── model_comparison.png
    └── fraud_dashboard.png
```

---

## ⚙️ How to Run

**Step 1 – Install dependencies:**
```bash
pip install -r requirements.txt
```

**Step 2 – Run the main ML pipeline:**
```bash
python fraud_detection_main.py
```

**Step 3 – Run Big Data pipeline:**
```bash
python bigdata_pipeline.py
```

**Step 4 – Generate dashboard:**
```bash
python dashboard.py
```

All charts and CSV outputs will appear in `reports/` and `data/` folders.

---

## 🧠 Algorithms Used

| Algorithm              | Type           | Purpose                          |
|------------------------|----------------|----------------------------------|
| Logistic Regression    | Supervised     | Baseline binary classification   |
| Decision Tree          | Supervised     | Interpretable fraud rules        |
| Random Forest          | Supervised     | Best accuracy + feature ranking  |
| Isolation Forest       | Unsupervised   | Anomaly detection (no labels)    |
| Rule-based Engine      | Heuristic      | Real-time flagging at scale      |

---

## 📊 Dataset Features

| Feature               | Description                                    |
|-----------------------|------------------------------------------------|
| `age`                 | Age of the beneficiary                         |
| `annual_income`       | Declared annual income (₹)                    |
| `family_size`         | Number of family members                       |
| `land_holding_ac`     | Agricultural land in acres                     |
| `scheme_amount`       | Amount claimed under the scheme (₹)           |
| `claims_per_year`     | Number of claims filed per year                |
| `distance_km`         | Distance from scheme office (km)              |
| `bank_txn_count`      | Bank transactions in last 6 months             |
| `duplicate_aadhaar`   | Whether Aadhaar is linked to multiple records  |
| `ghost_beneficiary`   | Deceased/non-existent beneficiary flag         |
| `scheme_type`         | PM-KISAN / MGNREGS / PMAY / Ration / Scholar  |
| `state`               | Indian state of the beneficiary                |

**Engineered Features:**
- `income_per_member` – Per capita income
- `claim_to_income` – Claim ratio (fraud if very high)
- `suspicious_score` – Composite rule-based fraud score

---

## 🚨 Fraud Indicators Detected

1. **Income too high** for welfare eligibility
2. **Excess claims** per year (>6)
3. **Invalid age** (<5 or >100 years)
4. **Duplicate Aadhaar** linked to multiple accounts
5. **Ghost beneficiaries** (deceased/fake persons)
6. **Unusually high scheme amounts**
7. **Zero bank transactions** (money not reaching beneficiary)

---

## 📈 Model Results (on 10,000 records)

| Model               | Accuracy | ROC-AUC |
|---------------------|----------|---------|
| Logistic Regression | ~92%     | ~0.97   |
| Decision Tree       | ~94%     | ~0.96   |
| Random Forest       | ~97%     | ~0.99   |

---

## 🗺️ Big Data Architecture

```
Raw Data (HDFS/S3)
       │
       ▼
  Spark Ingestion
       │
       ├──► MapReduce Aggregation  (state/scheme summaries)
       ├──► Streaming Deduplication (Aadhaar duplicate check)
       ├──► Rule-based Flagging Engine (vectorized filters)
       └──► ML Scoring Pipeline (Random Forest)
                │
                ▼
         Risk-Labeled Output → Dashboard / Alert System
```

---

## 🛠️ Tech Stack

- **Python 3.10+**
- **pandas, numpy** – Data manipulation
- **scikit-learn** – ML models, evaluation
- **matplotlib, seaborn** – Visualization
- **Apache Spark (PySpark)** – Big Data processing (pseudocode included)
- **HDFS / Kafka** – Distributed storage & streaming (reference architecture)

---

## 👨‍💻 Author

**[Your Name]**  
**[Your Roll Number]**  
**[Department / College Name]**  
Academic Year: 2024-25

---

*This is an academic project. The dataset is synthetically generated for demonstration purposes.*
