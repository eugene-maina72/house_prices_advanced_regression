## Ames Housing – Advanced Regression Techniques

### Overview
- Built an end-to-end CRISP-DM workflow to predict Ames, Iowa home prices for the Kaggle “House Prices: Advanced Regression Techniques” competition.
- Final tuned XGBoost model explains ~93% of price variance with RMSE ≈ \$19,837 on validation, outperforming baseline linear and tuned random forest models.
- Outputs include the full exploratory notebook, competition submission file, experiment tracking via MLflow, and supporting visuals.

### Repository Structure
- `notebook.ipynb` — primary analysis, feature engineering, model training, and evaluation.
- `data/` — Kaggle training/testing data, generated `house_price_submission.csv`, and provided descriptions.
- `images/` — figures for missingness, correlations, feature effects, and model metrics.
- `mlruns/` — MLflow experiment artifacts (models, metrics, parameters).
- `LICENSE`, `.gitignore`, `CONTRIBUTION.md`, `presentation_nontechnical.md`, `README.md`.

### Data & Problem
- Dataset: 1,460 training homes, 81 mixed-type features; target `SalePrice`.
- Evaluation: Root Mean Squared Error on log-transformed prices (competition metric).
- Files: `data/train.csv`, `data/test.csv`, `data/sample_submission.csv`, `data/data_description.txt`.

### Approach (CRISP-DM)
1) **Business Understanding** — pricing accuracy for real-estate stakeholders; minimize log-scale RMSE.
2) **Data Understanding** — explored missingness, outliers, neighborhood effects, temporal patterns, and key drivers (quality, size, location).
3) **Data Preparation** — domain-informed imputations, binary flags for heavy missingness, neighborhood-based `LotFrontage`, 11 engineered features, removal of 14 extreme outliers, scaling + one-hot encoding, feature selection.
4) **Modeling** — compared baseline Linear Regression, tuned Random Forest, and tuned XGBoost (Optuna search).
5) **Evaluation** — holdout validation; improvement and overfitting analysis; MLflow tracking for reproducibility.
6) **Deployment Outputs** — saved test-set predictions to `data/house_price_submission.csv` and logged final model to MLflow.

### Key Results
- **Linear Regression (baseline):** R² 0.883, RMSE \$25,226, MAE \$17,670.
- **Random Forest (tuned):** R² 0.897, RMSE \$23,665, MAE \$15,741.
- **XGBoost (tuned, final):** R² 0.928, RMSE \$19,837, MAE \$13,626; minimal overfitting (train–val R² gap ≈ 0.06).
- Important signals: overall quality, above-grade living area, neighborhood tiers (NridgHt/NoRidge/StoneBr premium), and quality×size interactions.

### Getting Started
**Prerequisites**
- Python 3.10+ recommended.
- Install dependencies: `pip install -U pandas numpy scikit-learn xgboost optuna mlflow matplotlib seaborn`
  - Optional but useful: `jupyterlab` or `notebook` for interactive runs.

**Reproduce the analysis**
1) Create/activate a virtual environment.
2) Install dependencies (above).
3) Launch the notebook: `jupyter notebook notebook.ipynb` (or open in VS Code).
4) Run cells sequentially; outputs include charts in `images/`, MLflow runs under `mlruns/`, and the generated `data/house_price_submission.csv`.

**MLflow**
- MLflow runs are configured in the notebook; to inspect, run `mlflow ui` from the project root and open the provided URL.

### Deliverables
- `notebook.ipynb` — documented CRISP-DM pipeline.
- `data/house_price_submission.csv` — competition predictions (1,459 homes).
- `images/` — visual summaries (missingness, correlations, feature effects, model metrics).
- `mlruns/` — experiment tracking for Linear Regression, Random Forest, XGBoost.

### Contributing
See `CONTRIBUTION.md` for issue/PR guidance, environment setup, and review expectations.

### License
MIT License. Kaggle data provided under competition terms (`data/data_description.txt`).

### Author
Eugene Maina | ML Engineer | Data Scientist

[Email](eugenemaina72@gmail.com) | [GitHub](https://github.com/eugene-maina72) | [LinkedIn](https://www.linkedin.com/in/eugene-maina-4a8b9a128/)