# Predicting Vehicle Fuel Efficiency Using Basic Regression Models

Group 13 project for IAI600 — Introduction to AI and Automation,
MSc in AI and Automation, University West.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/nippysky/auto-mpg-fuel-efficiency-prediction/blob/main/Auto_MPG_Group13_Project.ipynb)

## Project overview

This project predicts vehicle fuel efficiency, measured in miles per
gallon (MPG), using the UCI Auto MPG dataset.

We compare Linear Regression, Decision Tree and Random Forest models
against a baseline that predicts the mean training MPG. The aim is to
understand and apply a complete basic machine-learning workflow.

## How to run

1. Click the **Open in Colab** button above.
2. Sign into a Google account if required.
3. Connect to a standard Python CPU runtime. A GPU is not required.
4. Select **Runtime → Run all**.
5. Allow every cell to finish, including the hyperparameter search.

No manual dataset upload or Google Drive mounting is required.
The notebook downloads the dataset automatically from UCI.

A successful run ends with:

**Results saved successfully.**

Run the notebook from top to bottom in a fresh runtime to avoid
depending on variables left over from an earlier session.

## Dataset

- **Source:** [UCI Auto MPG](https://archive.ics.uci.edu/dataset/9/auto+mpg)
- **Records:** 398
- **Target:** Fuel efficiency in MPG
- **Predictors:** Cylinders, displacement, horsepower, weight,
  acceleration time, model year and origin
- **Missing data:** Six missing horsepower values
- **Excluded field:** Car name

Missing numerical values are filled using training-data medians.
Numerical features are standardized, and origin is one-hot encoded.
Preprocessing is included inside each model pipeline.

Dataset reference:
R. Quinlan, “Auto MPG,” UCI Machine Learning Repository, 1993.
https://doi.org/10.24432/C5859H

## Method

- Split the data into 318 training records and 80 test records.
- Use random seed 42.
- Explore the training data.
- Compare a mean baseline and three regression models using
  five-fold cross-validation.
- Search 36 Random Forest hyperparameter configurations.
- Select the final model using mean cross-validation RMSE.
- Evaluate the selected model and baseline on the test partition.
- Inspect prediction errors and training-data permutation importance.
- Demonstrate prediction for one hypothetical vehicle.

## Recorded results

The selected model is a tuned Random Forest with:

- 100 trees
- Maximum depth of 10
- Minimum leaf size of 1
- Square-root feature sampling

Its mean cross-validation RMSE is approximately **2.907 MPG**.

| Model | Test RMSE (MPG) | Test MAE (MPG) | Test R² |
|---|---:|---:|---:|
| Tuned Random Forest | 2.182 | 1.620 | 0.911 |
| Mean baseline | 7.347 | 5.955 | -0.004 |

These are the saved results for the specified split.
R² is not percentage accuracy. Small numerical differences may occur
with different software versions.

## Files and generated outputs

- `Auto_MPG_Group13_Project.ipynb`: complete project notebook.
- `README.md`: project description and running instructions.

Running the notebook creates:

- `data/`: downloaded dataset.
- `figures/`: exploratory plots, model comparison, prediction
  diagnostics and feature importance.
- `results/`: evaluation tables, individual predictions,
  split membership, feature importance and `environment.json`.

Generated files are stored in the Colab runtime. They are not
automatically committed to GitHub and should be downloaded before
the runtime is deleted.

## Tools

Python, NumPy, pandas, Matplotlib and scikit-learn, using Google Colab.

Step 15 records the Python and library versions used during execution
in `results/environment.json`.

## Limitations

The dataset is small and historical, so the results should not be
interpreted as validated predictions for modern vehicles.

The same test split was inspected during earlier project iterations.
The final notebook selects models using cross-validation, but its
test results describe a previously inspected holdout.

Permutation importance is calculated on training data. It describes
model reliance on the inputs and does not establish causation.

The hypothetical-vehicle prediction has no known target value and
therefore provides no additional accuracy measurement.

## Acknowledgment

Claude and ChatGPT assisted with code development, explanations and
debugging. The group remains responsible for understanding,
checking and explaining the submitted work.

We acknowledge the UCI Machine Learning Repository for the dataset
and the developers of the open-source libraries used.
