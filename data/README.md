# Data provenance and scope

No data files are stored in this repository. The notebook loads two datasets that are bundled with scikit-learn:

- `load_breast_cancer`: an educational binary-classification dataset with 569 observations and 30 numeric features.
- `load_diabetes`: an educational regression dataset with 442 observations, 10 standardized baseline features, and a quantitative target.

The notebook also embeds small numerical values from the supplied PDF references:

- A 100-email confusion matrix (TP = 40, TN = 45, FP = 5, FN = 10).
- Five actual and predicted length-of-stay values.

The PDF values are reference calculations only; they are not the scikit-learn training datasets. Neither the reference values nor the built-in datasets should be used for clinical, diagnostic, or operational decisions.
