# Machine Learning Model Evaluation: Classification Metrics and Regression Diagnostics

**Student:** Abrham Geberemedhin  
**Student ID:** WOUR/0082/16  
**GitHub repository:** [abrilohd/ML_Assignments](https://github.com/abrilohd/ML_Assignments)

## Purpose

This university assignment separates two related activities:

1. Verifying classification and regression calculations from supplied educational PDF examples.
2. Training and evaluating reproducible baseline models on independent built-in scikit-learn datasets.

The distinction matters: a confusion matrix or a list of predictions can be used to calculate metrics, but model evaluation additionally requires data preparation, fitting on training data, and evaluation on separate test data.

## Learning objectives

- Calculate and interpret accuracy, precision, recall, specificity, and F1-score.
- Calculate and interpret residuals, MAE, MSE, RMSE, and R-squared.
- Explain why a single metric is insufficient for model evaluation.
- Train baseline classification and regression models with reproducible train/test splits.
- Prevent preprocessing leakage by using scikit-learn pipelines.
- Communicate valid conclusions and limitations from small educational examples.

## What the notebook implements

### A. PDF reference calculations

The notebook reproduces and verifies two supplied examples:

- **Email filtering classification:** TP = 40, TN = 45, FP = 5, FN = 10. It verifies accuracy = 85%, precision = 88.89%, recall = 80%, specificity = 90%, and F1-score = 84.21%.
- **Patient length-of-stay regression:** five supplied actual/predicted values. It verifies MAE = 1.4, MSE = 2.6, and RMSE ≈1.61.

The regression PDF reports R-squared = 75.93% using a total sum of squares of 54. Direct calculation from its listed actual values gives squared deviations of 9, 1, 16, 25, and 1: total sum of squares = 52. With residual sum of squares = 13, the correct value is **R-squared = 1 - 13/52 = 75.00%**.

These are reference calculations, not trained models or new experimental data.

### B. Independent machine-learning experiments

- **Classification:** Logistic Regression is fitted to scikit-learn's built-in Wisconsin Diagnostic Breast Cancer dataset. `StandardScaler` and the model are combined in a pipeline, fitted only on the training partition, and evaluated on a stratified held-out test set. The positive class is encoded as malignant only to illustrate binary metrics; this is an educational experiment, not a diagnostic tool.
- **Regression:** Linear Regression is fitted to scikit-learn's built-in diabetes dataset. A pipeline is trained on a held-out split and evaluated with MAE, MSE, RMSE, R-squared, actual-versus-predicted, and residual plots. This dataset is not the PDF's patient length-of-stay dataset and supports no clinical or operational conclusion.

### C. Engineering practices

The notebook uses descriptive variables, fixed random states, checks for dimensions and missing values, safe division for undefined metrics, pipeline-based preprocessing, held-out evaluation, assertions for PDF arithmetic, and labeled plots.

## Metrics

- **Accuracy:** fraction of all classifications that are correct.
- **Precision:** fraction of predicted positives that are truly positive.
- **Recall (sensitivity):** fraction of actual positives that are detected.
- **Specificity:** fraction of actual negatives that are correctly identified.
- **F1-score:** harmonic mean of precision and recall.
- **MAE:** average absolute prediction error, in the target's units.
- **MSE:** average squared prediction error, which penalizes larger errors more strongly.
- **RMSE:** square root of MSE, returned to the target's units.
- **R-squared:** proportion of variation explained relative to predicting the target mean for the evaluated data.

## Project structure

```text
ML_Assignment/
├── ML_Assignment.ipynb   # Primary assignment notebook
├── README.md             # Project guide
├── requirements.txt      # Local execution dependencies
├── data/
│   └── README.md         # Data provenance and scope
└── outputs/
    └── .gitkeep          # Reserved for optional exports
```

## Local setup and execution

From the project directory in Windows PowerShell:

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
jupyter notebook ML_Assignment.ipynb
```

In Jupyter, choose **Kernel -> Restart Kernel and Run All Cells**. The notebook needs no local dataset files, absolute paths, secret, or API key.

## Google Colab

1. Upload `ML_Assignment.ipynb` to Google Colab, or choose **File -> Open notebook -> GitHub** and open it from [abrilohd/ML_Assignments](https://github.com/abrilohd/ML_Assignments).
2. Choose **Runtime -> Run all**.

Colab includes the required scientific Python packages in standard runtimes. The project repository is [github.com/abrilohd/ML_Assignments](https://github.com/abrilohd/ML_Assignments). The notebook uses built-in scikit-learn datasets and portable paths, so it does not require the original Windows folder.

## Reproducibility and limitations

`RANDOM_STATE = 42` fixes the data splits. The trained-model results are reproducible in a compatible scikit-learn environment, but model metrics can change if the dataset version, package version, split strategy, or random state changes.

- The PDF case studies are very small educational examples and cannot validate a model.
- The two scikit-learn datasets are independent teaching datasets, not data from the PDFs.
- One baseline model and one held-out split are appropriate for this course exercise, not evidence of optimal performance, fairness, calibration, or deployment readiness.
- The assignment does not diagnose patients or predict real hospital length of stay.

## References

1. *Classification Model Evaluation: Case Study Solutions*. Supplied educational reference PDF.
2. *Regression Model Diagnostics: Patient Length of Stay Case Study*. Supplied educational reference PDF.
3. scikit-learn developers, built-in `load_breast_cancer` and `load_diabetes` datasets.
