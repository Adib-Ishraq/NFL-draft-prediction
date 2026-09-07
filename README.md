# NFL Draft Prediction — GCI World 2026 April

Binary classification: predict whether a college athlete will be selected in the
NFL Draft (`Drafted`: 1 = drafted, 0 = not drafted) from combine performance
metrics, position, and body measurements.

**Metric:** ROC-AUC
**Competition:** GCI World 2026 April (Omnicampus)

## Data

| Column | Description |
|---|---|
| Id | Unique player ID |
| Year | Record year |
| Age | Player age |
| School | School name |
| Height / Weight | Body measurements |
| Sprint_40yd | 40-yard dash time |
| Vertical_Jump | Vertical jump reach |
| Bench_Press_Reps | Bench press repetitions |
| Broad_Jump | Broad jump distance |
| Agility_3cone | 3-cone drill time |
| Shuttle | 20-yard shuttle time |
| Player_Type / Position_Type / Position | Role/position info |
| Drafted | Target (train only) |

Raw data isn't tracked in this repo — see `data/README.md` for how to get it.

## Structure

## Setup
```bash
python -m venv venv
source venv/bin/activate   # Windows: venv\Scripts\activate
pip install -r requirements.txt
```

## Approach / notes
- Baseline: Random Forest, 5-fold stratified CV, AUC ≈ 0.8115 (0.813 with a `BMI = Weight / Height²` feature).
- Next steps: try LightGBM/XGBoost/CatBoost, better missing-value imputation (group-wise or KNN), target/frequency encoding for categoricals (including `School`), feature interactions.
