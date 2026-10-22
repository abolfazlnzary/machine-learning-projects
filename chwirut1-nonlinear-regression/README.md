# Ultrasonic Response Prediction — Non-Linear Regression

An educational comparison of Linear Regression and a nonlinear function using the NIST Chwirut1 dataset.

## Question and data

Can metal distance predict ultrasonic response? The included CSV contains 214 observations. `Metal_Distance` is the only input, `Ultrasonic_Response` is the target, and `Tag` is excluded from modeling. Distance ranges from 0.5 to 6; no missing values were found.

Dataset reference: [NIST Chwirut1](https://www.itl.nist.gov/div898/strd/nls/data/chwirut1.shtml). The included CSV uses renamed columns and an additional Tag column; it is not the original NIST text format. The local CSV's conversion provenance is not documented.

## Method

An 80/20 random split with `random_state=42` gives 171 training and 43 test observations. Both models use the same split. The nonlinear model is fitted only on training data using SciPy `curve_fit`:

```text
response = exp(-alpha * distance) / (A + B * distance)
initial_guess = [0.1, 0.01, 0.01]
```

Learned parameters: alpha ≈ 0.180727, A ≈ 0.005907, B ≈ 0.010868. These describe the mathematical curve; no specific physical interpretation is asserted.

## Test results

| Model | MAE | MSE | RMSE | R² |
| --- | ---: | ---: | ---: | ---: |
| Linear Regression | 11.070075 | 151.334783 | 12.301820 | 0.717150 |
| Non-Linear Regression | 2.096731 | 10.294767 | 3.208546 | 0.980759 |

The nonlinear model reduces test MAE by about 81%. Linear residuals show a curved pattern, which is substantially reduced by the nonlinear model. Residual spread remains larger at short distances. R² is not classification accuracy.

At distance 2.5 the fitted model predicts about 19.24 (interpolation). At distance 8 it predicts about 2.54 (extrapolation); its accuracy outside the observed range is unverified.

## Run in VS Code

Open this project folder and use Python 3.13:

```powershell
python -m venv .venv
.\.venv\Scripts\python.exe -m pip install -r requirements.txt
```

Install Microsoft's Python and Jupyter VS Code extensions. Open `nonlinear_regression.ipynb`, select the `.venv` kernel, and run cells from top to bottom. Keep the CSV beside the notebook.

## Learning and limitations

The notebook covers inspection, scatter plots, a linear baseline, nonlinear parameter fitting, predictions, metrics, and residual analysis. Polynomial Regression can draw a curved graph while remaining linear in its coefficients; this model is nonlinear in its learned parameters.

Results describe one random split, not a guarantee on future measurements. The model is unconstrained, initial guesses can affect convergence, and extrapolation is not validated. The meaning of Tag and potential dependence between observations have not been investigated.
