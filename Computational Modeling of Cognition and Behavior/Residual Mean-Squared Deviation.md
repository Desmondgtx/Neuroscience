Residual Mean-Squared Deviation (RMSD) measures the difference between two dataset, generally a model set and a observed set. It is used to determine how well a model fits the data:

The RMSD represents the average deviation of the data points from the predicted function:
$$RMSD = \sqrt{\frac {Σ_{i=1}^n (X_{obs,i} - X_{model,i})^2 } {n} }$$
**Where:**
- Observed: Actual data points
- Model: Model predictions
- n = number of data points

**How it's applied:**
1) For each data point
2) Sum all squared differences
3) Divide by the number of points
4) Take the square root

**Comparing models:**
Generally the model with lower RMSD fits better

