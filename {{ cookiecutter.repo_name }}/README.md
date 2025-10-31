# 🧠 {{ cookiecutter.project_name }}

{{ cookiecutter.description }}

---

## 📦 Overview

This repository was created from the [ML Template](https://github.com/jainmilan/ml-template) — a standardized structure for reproducible ML and DL research projects.  

It includes:
- A clean directory layout for data, code, and outputs  
- Ready-to-use experiment management with **Hydra**  
- Integrated **Poetry** environment for reproducibility  
- Optional experiment tracking with **MLflow**  
- Built-in support for **Optuna** (hyperparameter optimization)

---

## 🚀 Getting Started

### 1️⃣ Create the environment
```bash
poetry install
```

If you need deep learning support (PyTorch, Transformers, Lightning):
```bash
poetry install --with dl
```

Activate the environment:
```bash
poetry shell
```

---

### 2️⃣ Explore the data
```bash
jupyter lab
```

You can start from notebooks under `code/notebooks/` to perform exploratory data analysis (EDA) or visualize processed data.

---

### 3️⃣ Run training

The main training entry point is:

```bash
poetry run python code/src/training/train_model.py
```

You can customize experiments using **Hydra** configuration overrides, for example:
```bash
poetry run python code/src/training/train_model.py model=xgboost data=resstock train=default
```

Hydra automatically creates time-stamped output folders under `output/logs/` and can integrate with MLflow if configured.

---

### 4️⃣ Track results

If MLflow tracking is enabled in your config (`output/mlflow/`):
- All metrics, parameters, and model artifacts are logged automatically  
- You can visualize runs with:
  ```bash
  poetry run mlflow ui --backend-store-uri output/mlflow
  ```

Then open [http://localhost:5000](http://localhost:5000) in your browser.

---

## 📂 Project Structure

```
project/
├── code/
│   ├── src/
│   │   ├── data/            # Data loading & preprocessing scripts
│   │   ├── models/          # ML or DL model definitions
│   │   ├── training/        # Training & evaluation logic
│   │   ├── utils/           # Helper functions & metrics
│   │   └── visualization/   # Plotting utilities
│   ├── conf/                # Hydra configuration files
│   ├── notebooks/           # Exploratory analysis
│   ├── scripts/             # CLI utilities, batch jobs
│   └── tests/               # Unit tests
│
├── data/
│   ├── raw/                 # Immutable source data
│   ├── interim/             # Cleaned/intermediate datasets
│   └── processed/           # Ready-to-model data
│
├── output/
│   ├── logs/                # Hydra logs
│   ├── mlflow/              # MLflow experiments
│   ├── models/              # Saved models
│   ├── predictions/         # Model predictions
│   └── figures/             # Generated visualizations
│
├── documents/               # Reports, references, notes
├── presentations/           # Slide decks & figures
├── submissions/             # Paper drafts, reviews
├── pyproject.toml           # Poetry environment definition
├── README.md
└── Makefile                 # Common automation commands
```

---

## ⚙️ Configuration (Hydra)

Hydra makes it easy to manage configurations for:
- `data/` (dataset paths, splits)
- `model/` (architecture, hyperparameters)
- `train/` (epochs, batch size, early stopping)
- `eval/` (metrics, cross-validation)

Example `code/conf/config.yaml`:
```yaml
defaults:
  - data: resstock
  - model: xgboost
  - train: default

experiment_name: "building_energy_pred"
seed: 42
```

To override values on the fly:
```bash
python code/src/training/train_model.py train.batch_size=128 model.params.max_depth=5
```

---

## 🧮 Running Hyperparameter Sweeps

This project supports [Optuna](https://optuna.org/) for optimization via Hydra sweepers:

```bash
python code/src/training/train_model.py -m train.lr=0.001,0.01,0.1 train.batch_size=32,64
```

Results and best configurations are logged to MLflow.

---

## 📊 Outputs

All results are automatically organized under `output/`:

| Folder | Description |
|---------|--------------|
| `logs/` | Hydra run logs |
| `mlflow/` | Experiment tracking and metrics |
| `models/` | Trained model weights |
| `predictions/` | Generated predictions |
| `figures/` | Visualizations, plots, and reports |

---

## 🧠 Tips

- Keep all raw datasets under `data/raw/` (never modified manually).  
- Store processed or derived datasets under `data/processed/`.  
- Add any local paths or credentials to `.env` (not versioned).  
- Use `make setup`, `make run`, or `make clean` for quick automation.  
- Commit your `poetry.lock` file for reproducibility.

---

## 🧾 License

This project is distributed under the [MIT License](LICENSE).

---

## ✍️ Author

**{{ cookiecutter.author_name }}**

Built using the [ML Template](https://github.com/jainmilan/ml-template)  
for reproducible research and AI model development.