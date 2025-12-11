## Contribution Guidelines

Thank you for improving the Ames Housing regression project. Please follow these lightweight practices to keep changes clear and reproducible.

### How to Propose Changes
- Open an issue for significant changes (new features, refactors, data handling).
- Use feature branches (`feature/<short-description>`) and open a pull request.
- Keep PRs focused and small; include a short rationale and screenshots for UI/plot updates.

### Environment Setup
- Python 3.10+.
- Install dependencies: `pip install -U pandas numpy scikit-learn xgboost optuna mlflow matplotlib seaborn`
- Optional tools: `jupyterlab`/`notebook` for running `notebook.ipynb`; `mlflow ui` for browsing experiments.

### Development Expectations
- Prefer clear, self-documenting code; add concise comments only when logic is non-obvious.
- Follow PEP 8 style for Python.
- Keep data paths relative to the repository (e.g., `data/`); do not commit new raw data unless necessary.
- When touching modeling steps, describe the intent (e.g., feature added, tuning change) in the PR.

### Testing & Validation
- Run the relevant notebook sections before submitting to confirm cells execute cleanly and outputs are regenerated (plots, metrics, submission file).
- If you change preprocessing or modeling, note the impact on validation metrics and any MLflow run IDs.

### Review Checklist
- [ ] Code and notebook cells run without errors.
- [ ] README/`presentation_nontechnical.md` updated if user-facing behavior or findings change.
- [ ] No secrets or credentials are added.
- [ ] Large artifacts are ignored via `.gitignore`; keep only necessary outputs (submission CSV, key plots).
