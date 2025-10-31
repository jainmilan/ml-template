# 📦 ML Template

**A clean, reproducible, and scalable project template for AI and ML research — built with [Cookiecutter](https://cookiecutter.readthedocs.io/), [Poetry](https://python-poetry.org/), and [Hydra](https://hydra.cc/).**

This template lets you spin up new research projects in seconds, with a consistent environment, experiment tracking, and data organization structure that scales from exploratory ML to full DL workflows.

---

## 🚀 Quick Start

### 1️⃣ Generate a new project

```bash
cookiecutter gh:jainmilan/ml-template
```

You’ll be prompted for:
```
project_name [My ML Project]:
repo_name [my-ml-project]:
author_name [Milan Jain]:
description [A new ML project created from ml-template]:
python_version [3.10]:
```

This creates a new folder like:
```
my-ml-project/
├── code/
├── data/
├── output/
├── documents/
├── presentations/
└── submissions/
```

---

### 2️⃣ Set up the environment

Inside your generated project:

```bash
cd my-ml-project
poetry install
```

✅ This will:
- Create an isolated virtual environment  
- Install the ML research stack (NumPy, Pandas, Hydra, MLflow, Optuna, DVC, etc.)

---

### 3️⃣ Run your first experiment

```bash
poetry run python code/src/training/train_model.py
```

Use Hydra configs for flexible experimentation:

```bash
poetry run python code/src/training/train_model.py model=xgboost data=resstock train=default
```

---

## 🧱 Project Structure

```
{{ cookiecutter.repo_name }}/
├── code/
│   ├── src/
│   │   ├── data/              # Data loading & preprocessing
│   │   ├── models/            # ML/DL model definitions
│   │   ├── training/          # Training and evaluation logic
│   │   ├── utils/             # Reusable helper functions
│   │   └── visualization/     # Plotting & analytics
│   ├── conf/                  # Hydra configuration files
│   ├── notebooks/             # EDA & analysis notebooks
│   ├── scripts/               # CLI utilities or batch jobs
│   └── tests/                 # Unit tests
│
├── data/
│   ├── raw/                   # Immutable input data
│   ├── interim/               # Cleaned/intermediate data
│   └── processed/             # Ready-to-use datasets
│
├── output/
│   ├── logs/                  # Logs from training
│   ├── mlflow/                # MLflow experiment runs
│   ├── models/                # Saved models
│   ├── predictions/           # Model outputs
│   └── figures/               # Visualizations
│
├── documents/                 # Reports, references, notes
├── presentations/             # Slides and figures
├── submissions/               # Papers and revisions
├── pyproject.toml             # Poetry environment
├── .gitignore
├── README.md
└── Makefile                   # Common automation tasks
```

---

## ⚙️ Key Features

| Capability | Description |
|-------------|--------------|
| 🧩 **Modular project structure** | Consistent organization for data, code, and outputs |
| 🧠 **Hydra configs** | Declarative, composable configuration for experiments |
| 📈 **MLflow tracking** | Log metrics, parameters, and models automatically |
| 🔍 **Optuna sweeps** | Built-in hyperparameter optimization |
| 🧮 **DVC-ready** | Version control for data and models |
| ⚡ **Optional DL layer** | Add PyTorch, Lightning, and Transformers via Poetry groups |
| 🧰 **Poetry-based dependency management** | Reproducible environments across systems |
| 🧑‍💻 **Cookiecutter automation** | Spin up new projects from this template instantly |

---

## 🧪 Optional: Install Deep Learning Dependencies

If your project involves DL models (PyTorch, Transformers, etc.):

```bash
poetry install --with dl
```

---

## 🧰 Makefile Commands

| Command | Description |
|----------|--------------|
| `make setup` | Install dependencies |
| `make run` | Run training script |
| `make clean` | Remove logs, outputs, and models |

---

## 🧠 Best Practices

1. Keep your **data/raw** immutable — never edit raw files manually.  
2. Log every experiment through **Hydra + MLflow** for reproducibility.  
3. Use **Poetry groups** to install only what’s necessary (`--with dl`, `--with dev`).  
4. Version control everything except raw data and heavy outputs.  
5. Periodically run `poetry update` to stay current with safe dependency versions.

---

## 🧾 License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for details.

---

## 🧠 Credits

Developed and maintained by **Milan Jain**  
Pacific Northwest National Laboratory (PNNL)  
For AI, data analytics, and simulation research workflows.