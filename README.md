# Predicting 10-Year Coronary Heart Disease Risk

This project was my take on tackling a classic, real-world clinical problem: predicting the 10-year risk of coronary heart disease (CHD) using data from the Framingham Heart Study.

The dataset's main challenge isn't its complexity, but its severe class imbalance. With only about 15% of individuals developing CHD, building a model that does more than just guess "no disease" is surprisingly difficult.

## My Process

The project is split into a few notebooks that follow my workflow.

1. notebooks/eda.ipynb:
Getting to know the data: This is the foundational deep dive. Before any modeling, I focused on cleaning the data, visualizing the distributions, and using statistical tests to figure out which features had a real, significant link to the CHD outcome.

2. notebooks/model_training.ipynb & model_training2.ipynb:
- My first attempt at modeling involved using SMOTE to artificially balance the training data. This is a common technique, but as model_training.ipynb shows, the results were not great. The models struggled to generalize.
- Realizing that approach wasn't working, I pivoted. The second notebook, model_training2.ipynb, documents a more careful approach, using model-level parameters (`class_weight` and `scale_pos_weight`) to handle the imbalance instead. This notebook contains the systematic hyperparameter tuning for all the final models.

## Key Takeaways

- My main finding was the classic accuracy vs. F1-score paradox. It was easy to get a model with >80% accuracy, but that number was misleading. The F1-scores for the positive class remained low (around 0.30-0.35), showing the models were still failing to identify most of the at-risk patients.
- WAs expected, clinical factors like Age, Systolic Blood Pressure, Total Cholesterol, and Glucose were consistently the most powerful predictors in the models.
- One of the most valuable parts of this project was discovering that many public notebooks on this dataset report very high scores. I realized a couple of them had a subtle methodological error: applying SMOTE before splitting the data, which causes data leakage and inflates the results.

Ultimately, this project shows that even with proper tuning, the predictive power of this particular dataset has its limits.

## How to Run

1.  Clone the repository.
2.  Set up a virtual environment and install the requirements:
    ``bash
    pip install -r requirements.txt
    ``
3.  Launch Jupyter and open the notebooks in the notebooks/ directory.