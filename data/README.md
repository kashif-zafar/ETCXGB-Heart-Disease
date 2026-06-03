# Dataset Instructions

## Dataset Not Included

The raw dataset is **not committed** to this repository (excluded via `.gitignore`).

## How to Obtain

**UCI Hungarian Heart Disease Dataset**

Download from the UCI ML Repository:
- https://archive.ics.uci.edu/ml/datasets/Heart+Disease



## Expected Format

Place the CSV file here as `data/dataset.csv`.

The file must have **exactly these 14 columns** in this order:

| Column | Description | Values |
|--------|-------------|--------|
| `age` | Age in years | Numeric |
| `sex` | Sex | 0 = Female, 1 = Male |
| `cp` | Chest pain type | 0–3 |
| `trestbps` | Resting blood pressure (mmHg) | Numeric |
| `chol` | Serum cholesterol (mg/dL) | Numeric |
| `fbs` | Fasting blood sugar > 120 mg/dL | 0 = False, 1 = True |
| `restecg` | Resting ECG results | 0–2 |
| `thalach` | Maximum heart rate achieved | Numeric |
| `exang` | Exercise induced angina | 0 = No, 1 = Yes |
| `oldpeak` | ST depression induced by exercise | Numeric |
| `slope` | Slope of peak exercise ST segment | 0–2 |
| `ca` | Number of major vessels (0–3) colored by fluoroscopy | 0–3 |
| `thal` | Thalassemia | 0 = Normal, 1 = Fixed defect, 2 = Reversible defect |
| `target` | Diagnosis of heart disease | 0 = No Disease, 1 = Disease |

## After Placing the Dataset

Update `FILE_PATH` in **Cell 1** of the notebook:

```python
FILE_PATH = 'data/dataset.csv'
```
