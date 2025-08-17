# personalized-nutrition-rowing
Official code for the paper: Data-Augmented Machine Learning for Personalized Carbohydrate-Protein Supplement Recommendation for Endurance.
# Data-Augmented Machine Learning for Personalized Carbohydrate-Protein Supplement Recommendation for Endurance

## Description

This repository contains the official code implementation for the paper, "Data-Augmented Machine learning for Personalized Carbohydrate-Protein Supplement Recommendation for Endurance." This project aims to develop and evaluate a predictive machine learning framework for generating personalized carbohydrate-protein supplement strategies to enhance endurance rowing performance.

The core methodological novelty lies in the application of a Wasserstein Generative Adversarial Network with Gradient Penalty (WGAN-GP) to address the common challenge of small sample sizes in sports science research. Through a rigorous evaluation pipeline, this work builds a personalized recommendation system that balances high predictive accuracy with model stability.

---

## Installation

All dependencies for this project are listed in the `environment.yml` file. It is highly recommended to use [Anaconda](https://www.anaconda.com/products/distribution) to create and manage the environment.

Please follow these steps to create an identical environment for this project:

1.  **Clone or download this repository to your local machine.**
2.  **Open Anaconda Prompt (on Windows) or Terminal (on macOS/Linux).**
3.  **Navigate to the project's root directory using the `cd` command.**
4.  **Run the following commands to create and activate the environment:**
    ```bash
    # Create a new environment named 'sports-nutrition' from the .yml file
    conda env create -f environment.yml

    # Activate the newly created environment
    conda activate sports-nutrition
    ```
The environment is now ready for use.

---

## Usage 🚀

To fully reproduce the results of this study, please run the Jupyter Notebooks in the `notebooks` folder in the following sequential order. Each notebook represents a distinct step in the analysis pipeline.

1.  `01_data_splitting.ipynb`
    * **Function**: Reads the raw dataset (`JM.xlsx`) and performs a stratified 80/20 split to generate the development and final test sets.

2.  `02_feature_selection.ipynb`
    * **Function**: A comprehensive feature selection notebook that includes three main steps:
        1.  Exploratory data analysis, including a correlation heatmap of the full dataset.
        2.  Feature importance ranking using an XGBoost model.
        3.  Application of the selection criteria to prune excess features from the development and test sets.

3.  `03_baseline_xgboost_training.ipynb`
    * **Function**: Trains and evaluates the baseline XGBoost model using the feature-selected development set.

4.  `04_baseline_mlp_training.ipynb`
    * **Function**: Trains and evaluates the baseline Multi-Layer Perceptron (MLP) model.

5.  `05_baseline_svr_training.ipynb`
    * **Function**: Trains and evaluates the baseline Support Vector Regression (SVR) model.

6.  `06_augmentation_wgan_gp.ipynb`
    * **Function**: Performs data augmentation on the feature-selected development set using WGAN-GP.

7.  `07_augmentation_traditional_methods.ipynb`
    * **Function**: Performs data augmentation using traditional methods (Mixup and Random Noise Injection).

8.  `08_eval_augmentation_correlation.ipynb`
    * **Function**: Evaluates the data augmentation methods by comparing correlation matrices.

9.  `09_eval_augmentation_mwu.ipynb`
    * **Function**: Evaluates the augmentation methods using the Mann-Whitney U test.

10. `10_eval_augmentation_kde.ipynb`
    * **Function**: Evaluates the augmentation methods by plotting and comparing Kernel Density Estimate (KDE) distributions.

11. `11_augmented_xgboost_training.ipynb`
    * **Function**: Trains and evaluates the augmented XGBoost model using the selected synthetic data.

12. `12_augmented_mlp_training.ipynb`
    * **Function**: Trains and evaluates the augmented MLP model.

13. `13_augmented_svr_training.ipynb`
    * **Function**: Trains and evaluates the augmented SVR model.

---

## Data Availability ⚠️

**Please Note**: The raw dataset (`JM.xlsx`) used in this study is not included in this repository, as it is derived from the author's doctoral thesis and is being used for ongoing research.

To run the code in this project, users must provide their own data file named **`JM.xlsx`** and place it in the **`data`** folder. This file must contain the following **47 features (columns)** with the exact same column headers listed below:

**Input Features (46):**
`Previous meal time`, `CHO`, `PRO`, `fat`, `sodium`, `magnesium`, `calcium`, `Age`, `Height`, `weight`, `Body water percentage`, `body fat percentage`, `Triceps skinfold`, `subscapular skinfold`, `suprailiac skinfold`, `abdominal skinfold`, `upper arm circumference`, `waist circumference`, `hip circumference`, `subgluteal thigh circumference`, `mid-thigh circumference`, `calf circumference`, `Deep sleep`, `light sleep`, `rapid eye movement`, `IES-2`, `PSQI`, `PARS – 3`, `Smoking frequency in the last 30 days`, `Alcohol use in the last 30 days`, `Resting heart rate`, `high blood pressure`, `low blood pressure`, `Blood glucose`, `blood lactate`, `hemoglobin`, `Left-hand grip strength`, `Right-hand grip strength`, `average vertical jump height before exercise`, `DC Potential`, `HF`, `LF`, `total power`, `SDNN`, `RMSSD`, `SDSD`

**Target / Output Feature (1):**
`Rowing distance`

**Important**: The target variable `Rowing distance` is hard-coded in several scripts. If you are using a dataset with a different target variable, you will need to modify this name within the code accordingly.
