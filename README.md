# ✈️ ML Assignment 4 — Pipeline

This repository trains and evaluates an **AdaBoost-based machine learning pipeline** for the **Airline Passenger Satisfaction** dataset.
It automates data ingestion, validation, transformation, model training, and evaluation — all driven by YAML configurations.

---

### What’s Included

#### **Root Files**

* **main.py** — orchestrates the full end-to-end pipeline (runs all stages sequentially)
* **app.py** — optional application script (for prediction or deployment)
* **params.yaml** — stores model hyperparameters
* **config.yaml** — controls file paths and component settings
* **schema.yaml** — defines the dataset structure for validation
* **requirements.txt** — dependencies list
* **README.md** — project overview and workflow

---

#### **src/** — main project modules

| File / Folder   | Description                                                                       |
| --------------- | --------------------------------------------------------------------------------- |
| **components/** | Each pipeline stage — ingestion, validation, transformation, training, evaluation |
| **config/**     | Configuration manager for loading YAML settings dynamically                       |
| **constants/**  | Global constants (paths, schema references, etc.)                                 |
| **entity/**     | Data classes for configuration and artifact entities                              |
| **pipeline/**   | Wrapper scripts to run each ML pipeline stage                                     |
| **utils/**      | Helper functions for saving models, reading YAMLs, etc.                           |

---

#### **artifacts/** — runtime outputs

Created automatically when you run `main.py`.
Stores:

* Intermediate datasets (`train.csv`, `test.csv`)
* Trained model file (`model.joblib`)
* Evaluation results (`metrics.json`)
* Logs and status reports

---

#### **research/**

Contains experimental Jupyter notebooks for testing data loading, transformation, training, and evaluation before formalizing them into the pipeline.

---

#### **logs/**

Contains structured runtime logs for debugging and audit trails.

---

###  Quick Setup

**PowerShell**

```powershell
# Create virtual environment
python -m venv .venv; .\.venv\Scripts\Activate.ps1

# Install dependencies
pip install -r requirements.txt
```

Ensure the dataset exists under:

```
artifacts/data_ingestion/airplane1.csv
```

---

###  Run the Full Pipeline

This executes data ingestion → validation → transformation → training → evaluation automatically.

**PowerShell**

```powershell
python main.py
```

**Outputs:**

* Processed data → `artifacts/data_transformation/`
* Model → `artifacts/model_trainer/model.joblib`
* Evaluation metrics → `artifacts/model_evaluation/metrics.json`

---

###  Logging Behavior

All logs are written to the `logs/` directory automatically during each pipeline run.

Typical structure:

```
logs/
├── running_log.log    # standard runtime logs
└── error_log.log      # optional error details if implemented
```

---

###  Troubleshooting

| Issue                                  | Fix                                                             |
| -------------------------------------- | --------------------------------------------------------------- |
| **Git push fails (large file >100MB)** | Use Git LFS or remove heavy artifacts before pushing            |
| **File path issues (Windows)**         | Use raw string paths, e.g., `r"C:\Users\..."`                   |
| **Model not saving**                   | Check artifact directory permissions and paths in `config.yaml` |
| **Module import errors**               | Verify you’re running from project root: `python main.py`       |

---

###  Notes

* Each stage runs independently, so you can test modules individually (e.g., run only Model Training or Evaluation).
* YAML-driven configuration allows flexible tuning without modifying the source code.
* The modular design makes it easy to extend with new algorithms, validation methods, or deployment steps later.

Would you like me to extend this with an **“Evaluation and SHAP Explanations”** section at the end — showing how SHAP is integrated for feature importance (like in your AdaBoost version)? It’ll make your README complete and ready for GitHub portfolio presentation.
