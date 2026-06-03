# ETCXGB — Explainable Heart Disease Prediction

A two-stage ensemble pipeline for heart disease prediction with full explainability analysis using SHAP, LIME, and clinical insights.

---

## Pipeline Overview

```
13 Clinical Features
        │
        ▼
┌───────────────────────┐
│  Stage 1: ExtraTrees  │  ──→  ET_Probability (disease risk score)
└───────────────────────┘
        │
        ▼ (13 original + ET_Probability = 14 features)
┌───────────────────────┐
│  Stage 2: XGBoost     │  ──→  Final Prediction + Probabilities
└───────────────────────┘
        │
        ▼
  Explainability Layer
  (SHAP · LIME · PDP · Clinical Reports)
```

**Dataset:** UCI Hungarian Heart Disease Dataset  
**Features:** `age · sex · cp · trestbps · chol · fbs · restecg · thalach · exang · oldpeak · slope · ca · thal`  
**Target:** Binary — `0` (No Disease) / `1` (Disease)

---

## Repository Structure

```
etcxgb-heart-disease/
│
├── ETCXGB_Full_Pipeline_Explainability.ipynb   # Main notebook (all stages)
│
├── data/
│   └── README.md                               # Dataset instructions
│
├── outputs/                                    # Generated plots land here
│   └── .gitkeep
│
├── assets/                                     # Architecture diagrams / docs
│   └── pipeline_diagram.md
│
├── requirements.txt
├── .gitignore
└── README.md
```

---

## Notebook Sections

| Section | Description |
|---------|-------------|
| **0. Setup** | Installs dependencies, imports |
| **1. Load Data & Build Pipeline** | Data loading, train/test split, StandardScaler, ETC + XGB training, metrics |
| **2. Confusion Matrix & ROC** | Side-by-side CM for both stages + comparative ROC curves |
| **3. SHAP Values** | TreeExplainer for both ETC and XGBoost |
| **4. Stage 1 — ETC Explainability** | Gini importance, SHAP beeswarm, single-patient waterfall |
| **5. Stage 2 — XGB Explainability** | Gain importance, SHAP beeswarm, waterfall (same patient) |
| **6. Pipeline Analysis** | SHAP comparison across stages, ET_Probability contribution, ETC–XGB agreement analysis, LIME dual explanation, dual waterfall |
| **7. Partial Dependence Plots** | Top-4 features PDP |
| **8. Medical Insights** | Feature ranking, clinical distributions, thresholds, categorical risk profiles, interaction plots, individual clinical reports, SHAP dependence with clinical reference lines |

---

## Output Files

**Performance**
- `performance_cm_roc.png`

**Stage 1 — ExtraTrees**
- `etc_feature_importance.png`
- `etc_shap_beeswarm.png`
- `etc_waterfall_p5.png`

**Stage 2 — XGBoost**
- `xgb_feature_importance_gain.png`
- `xgb_shap_beeswarm.png`
- `xgb_waterfall_p5.png`

**Pipeline Analysis**
- `pipeline_shap_comparison.png`
- `pipeline_et_contribution.png`
- `pipeline_agreement.png`
- `pipeline_dual_waterfall_p*.png`
- `pipeline_lime_dual_p*.png`

**PDP**
- `pdp_top4.png`

**Medical Analysis**
- `medical_feature_ranking.png`
- `medical_distributions.png`
- `medical_thresholds.png`
- `medical_categorical_risk.png`
- `medical_interactions.png`
- `medical_risk_profiles.png`
- `medical_shap_clinical.png`

---

## Setup & Usage

### 1. Clone the repo
```bash
git clone https://github.com/kashif-zafar/ETCXGB-Heart-Disease.git
cd ETCXGB-Heart-Disease
```

### 2. Install dependencies
```bash
pip install -r requirements.txt
```

### 3. Add the dataset
Place your CSV file inside `data/` and update the `FILE_PATH` variable in **Cell 1** of the notebook:
```python
FILE_PATH = 'data/dataset.csv'   # update this line
```



Upload the dataset when prompted, or mount Google Drive.

### 4. Run locally with Jupyter
```bash
jupyter notebook ETCXGB_Full_Pipeline_Explainability.ipynb
```

---

## Key Metrics (on UCI Hungarian dataset)

| Metric | Value |
|--------|-------|
| Accuracy | ~88–91% |
| Sensitivity | ~90%+ |
| Specificity | ~87%+ |
| ROC-AUC | ~0.94+ |
| MCC | ~0.77+ |

> Exact values depend on the dataset split and random seed.

---

## Tech Stack

| Library | Purpose |
|---------|---------|
| `scikit-learn` | ExtraTreesClassifier, preprocessing, metrics |
| `xgboost` | Stage 2 gradient boosting |
| `shap` | TreeExplainer, beeswarm, waterfall, dependence plots |
| `lime` | Local Interpretable Model-Agnostic Explanations |
| `matplotlib` / `seaborn` | Visualization |
| `pandas` / `numpy` | Data manipulation |

---

## Explainability Methods

- **SHAP (SHapley Additive exPlanations):** Global feature importance (beeswarm) and local patient-level explanations (waterfall) for both stages.
- **LIME:** Local surrogate model explanations for individual predictions across both stages.
- **Partial Dependence Plots (PDP):** Marginal effect of top features on predicted probability.
- **Clinical Reports:** Patient-level reports mapping model decisions to clinical meaning (ST depression, vessel count, thalassemia perfusion, etc.).

---

## Dataset

This project uses the **UCI Hungarian Heart Disease Dataset**.  
Download from: [UCI ML Repository](https://archive.ics.uci.edu/ml/datasets/Heart+Disease)

Expected columns (in order):
```
age, sex, cp, trestbps, chol, fbs, restecg, thalach, exang, oldpeak, slope, ca, thal, target
```

---



---

## Author

Built as part of the ETCXGB Major Project — JMI (Jamia Millia Islamia).

---

## Ground Paper

This implementation follows the approach proposed in the following paper (used as the ground paper for this project):

- Bilal, H., Tian, Y., Ali, A., Muhammad, Y., Yahya, A., Izneid, B. A., & Ullah, I. (2024). An intelligent approach for early and accurate predication of cardiac disease using hybrid artificial intelligence techniques.

BibTeX citation:

```bibtex
@article{bilal2024intelligent,
        author = {Bilal, H. and Tian, Y. and Ali, A. and Muhammad, Y. and Yahya, A. and Izneid, B. A. and Ullah, I.},
        title = {An intelligent approach for early and accurate predication of cardiac disease using hybrid artificial intelligence techniques},
        journal = {--},
        year = {2024}
}
```
