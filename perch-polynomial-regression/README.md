# Perch Weight Prediction — Polynomial Regression

A completed educational walkthrough comparing Linear Regression with Polynomial Regression to predict Perch fish weight using only `Length3`.

## Files

- `perch_regression.ipynb`: step-by-step learning notebook.
- `fish_perch_polynomial.csv`: 56 fish records; the model uses `Length3` as X and `Weight` as y.

## Current results

All models use the same 44 training samples and 12 test samples (`test_size=0.2`, `random_state=42`).

| Model | Train RMSE | Test RMSE | Train R² | Test R² |
| --- | ---: | ---: | ---: | ---: |
| Degree 1 | 85.189 | 138.873 | 0.939 | 0.834 |
| Degree 2 | 57.951 | 46.160 | 0.972 | 0.982 |
| Degree 3 | 55.920 | 65.890 | 0.974 | 0.963 |

Degree 2 performs best on this particular test split. The test set has been used for comparison, so these results are exploratory rather than an independent final evaluation.

Polynomial features add powers of length; Linear Regression then learns their coefficients. The resulting relationship can be curved while remaining linear in its coefficients.

## Run locally

Create and activate a virtual environment, then install:

```powershell
python -m pip install -r requirements.txt
```

Open the notebook with this environment as its kernel. Run cells in order with the notebook directory as the working directory.

## Learning status

Completed: data inspection, visualization, train/test split, Linear baseline, degrees 2 and 3, model comparison, underfitting discussion, degree 8 overfitting demonstration, residual analysis, model selection, prediction, extrapolation, and final conclusion.

Degree 8 achieved Train RMSE 48.54 but Test RMSE 1599.55, with a severe deviation at the short-length test point outside the training length range. Degree 2 was selected for this educational comparison. It predicts approximately 509.29 for Length3 = 35. The prediction of 4307.31 at Length3 = 80 is extrapolation and is not validated by the dataset.
