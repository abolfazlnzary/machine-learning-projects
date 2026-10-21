# Perch Weight Prediction — Polynomial Regression

An in-progress educational project comparing Linear Regression with Polynomial Regression to predict Perch fish weight using only `Length3`.

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

Completed so far: data inspection, visualization, train/test split, Linear baseline, degrees 2 and 3, and model comparison. Underfitting discussion is in progress. Overfitting demonstration, residual analysis, final model selection, new predictions, and extrapolation remain to be explored.
