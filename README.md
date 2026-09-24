# Kidney Disease Classification

> Deep Learning-based kidney disease classification from medical images with experiment tracking, data versioning, and reproducible ML pipelines.

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue?logo=python)](https://www.python.org/)
[![TensorFlow](https://img.shields.io/badge/TensorFlow-Deep%20Learning-orange?logo=tensorflow)](https://www.tensorflow.org/)
[![MLflow](https://img.shields.io/badge/MLflow-Experiment%20Tracking-blue)](https://mlflow.org/)
[![DVC](https://img.shields.io/badge/DVC-Data%20Versioning-purple)](https://dvc.org/)
[![Docker](https://img.shields.io/badge/Docker-Containerized-blue?logo=docker)](https://www.docker.com/)
[![GitHub Actions](https://img.shields.io/badge/GitHub%20Actions-CI%2FCD-black?logo=github)](https://github.com/features/actions)

---

## Overview

This project implements an end-to-end deep learning pipeline for **kidney disease classification using medical images**.

The system uses a Convolutional Neural Network (CNN) to learn visual patterns from kidney images and classify them into the supported disease categories.

The project is structured around reproducible machine learning practices, including:

* Deep learning-based image classification
* Modular Python code
* MLflow experiment tracking
* DVC-based data and pipeline versioning
* Configuration-driven training
* Model versioning
* Docker support
* GitHub Actions for automation
* Web-based prediction interface

The goal of the project is not only to train a model, but to demonstrate how a deep learning model can be organized into a reproducible ML workflow.

---

## Key Features

* 🧠 **CNN-based image classification**
* 📊 **MLflow experiment tracking**
* 🔄 **DVC pipeline and data versioning**
* ⚙️ **Configuration-driven training**
* 🧩 **Modular project architecture**
* 🌐 **Web-based prediction interface**
* 🐳 **Docker support**
* 🔁 **GitHub Actions workflow**
* 📁 **Reproducible training pipeline**
* 🔐 **Environment-based configuration for credentials**

---

## Tech Stack

| Category                   | Technology         |
| -------------------------- | ------------------ |
| Programming Language       | Python             |
| Deep Learning              | TensorFlow / Keras |
| Experiment Tracking        | MLflow             |
| Data & Pipeline Versioning | DVC                |
| Web Application            | Flask              |
| Containerization           | Docker             |
| CI/CD                      | GitHub Actions     |
| Version Control            | Git / GitHub       |

---

## Project Architecture

```text
                    ┌─────────────────────┐
                    │    Input Image      │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │   Data Processing   │
                    │  & Preprocessing    │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │    CNN Model        │
                    │ Training & Testing  │
                    └──────────┬──────────┘
                               │
                  ┌────────────┴────────────┐
                  ▼                         ▼
        ┌──────────────────┐      ┌──────────────────┐
        │     MLflow       │      │       DVC        │
        │ Experiment       │      │ Data & Pipeline  │
        │ Tracking         │      │ Versioning       │
        └──────────────────┘      └──────────────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │   Trained Model     │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │  Web Application     │
                    │   Image Prediction   │
                    └─────────────────────┘
```

---

## Repository Structure

```text
kidney-disease-classification-Platform/
│
├── .github/
│   └── workflows/          # GitHub Actions workflows
│
├── config/
│   └── config.yaml         # Project configuration
│
├── research/               # Experiments and development notebooks
│
├── src/
│   └── cnnClassifier/      # Core project modules
│
├── templates/              # Web application templates
│
├── model/                  # Trained model artifacts
│
├── .dvc/
├── .dvcignore
├── dvc.yaml                # DVC pipeline definition
├── dvc.lock                # DVC pipeline lock file
│
├── params.yaml             # Training parameters
├── requirements.txt        # Python dependencies
├── setup.py                # Package configuration
├── Dockerfile              # Docker configuration
├── app.py                  # Web application
├── main.py                 # Pipeline entry point
├── scores.json             # Model evaluation results
└── README.md
```

---

## Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/Kanak3064/kidney-disease-classification-Platform.git
cd kidney-disease-classification-Platform
```

### 2. Create a virtual environment

Using Conda:

```bash
conda create -n kidney-disease python=3.8 -y
conda activate kidney-disease
```

Or using Python's built-in virtual environment:

```bash
python -m venv venv
```

Activate it on Windows:

```bash
venv\Scripts\activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Run the application

```bash
python app.py
```

Then open:

```text
http://localhost:8080
```

> The exact port may depend on the configuration used by the application.

---

## ML Pipeline

The project follows a modular machine learning workflow:

```text
Configuration
     ↓
Data Ingestion
     ↓
Data Validation
     ↓
Data Transformation
     ↓
Model Training
     ↓
Model Evaluation
     ↓
Model Saving
     ↓
Prediction
```

Project parameters can be modified through:

```text
params.yaml
```

Project-level configuration is maintained through:

```text
config/config.yaml
```

---

## MLflow

MLflow is used for experiment tracking and model-related metadata.

Typical information tracked during experiments can include:

* Training parameters
* Model metrics
* Experiment runs
* Model artifacts

To start the local MLflow interface:

```bash
mlflow ui
```

Then open the URL displayed by MLflow in your browser.

### Remote MLflow Configuration

If you want to use a remote MLflow server, configure credentials through environment variables rather than committing credentials to GitHub.

Example:

```bash
MLFLOW_TRACKING_URI=<your_tracking_uri>
MLFLOW_TRACKING_USERNAME=<your_username>
MLFLOW_TRACKING_PASSWORD=<your_password>
```

**Never commit real credentials, API keys, passwords, or access tokens to the repository.**

---

## DVC

DVC is used to manage machine learning data and pipeline reproducibility.

Useful commands:

```bash
dvc init
```

Run the pipeline:

```bash
dvc repro
```

Visualize the pipeline:

```bash
dvc dag
```

Check the status of tracked files:

```bash
dvc status
```

---

## Model

The trained model is intentionally not stored directly in Git when the file size is too large for normal Git version control.

For a production implementation, model artifacts can be managed using:

* DVC
* Cloud object storage
* MLflow Model Registry
* Other dedicated model storage

---

## Running Predictions

The application accepts an input kidney image and passes it through the trained classification model.

The prediction workflow is:

```text
Input Image
     ↓
Image Validation
     ↓
Preprocessing
     ↓
CNN Model
     ↓
Prediction
     ↓
Result
```

---

## Docker

The project includes a `Dockerfile` for containerized execution.

Build the image:

```bash
docker build -t kidney-disease-classifier .
```

Run the container:

```bash
docker run -p 8080:8080 kidney-disease-classifier
```

Then open:

```text
http://localhost:8080
```

---

## CI/CD

GitHub Actions configuration is included under:

```text
.github/workflows/
```

The workflow can be used to automate tasks such as:

* Installing dependencies
* Running project checks
* Building Docker images
* Preparing deployment workflows

Cloud deployment requires configuring the appropriate credentials and infrastructure separately.

---

## Results

The project stores model evaluation information in:

```text
scores.json
```

For a production-quality version, additional evaluation metrics can be added here, such as:

* Accuracy
* Precision
* Recall
* F1-score
* Confusion Matrix
* ROC-AUC

---

## Screenshots

*Add application screenshots here.*

Recommended screenshots:

1. Application home page
2. Image upload interface
3. Prediction result
4. MLflow experiment dashboard

Example:

```text
docs/
├── application.png
├── prediction.png
└── mlflow.png
```

---

## Future Improvements

Planned improvements include:

* [ ] Improve model architecture and validation
* [ ] Add comprehensive model evaluation
* [ ] Add prediction confidence visualization
* [ ] Improve the web interface
* [ ] Add automated testing
* [ ] Improve Docker deployment
* [ ] Add production-grade logging
* [ ] Integrate a model registry
* [ ] Deploy the application to a cloud platform
* [ ] Add monitoring for deployed models

---

## Disclaimer

This project is intended for **educational and research purposes**.

Predictions generated by the model should not be considered a medical diagnosis. Any real-world clinical application would require appropriate medical validation, regulatory compliance, clinical testing, and expert oversight.

---

## Attribution

This repository is an independently maintained version based on an existing open-source/tutorial implementation by **Krish Naik**.

The project has been adapted for personal learning and portfolio development, including repository restructuring, documentation changes, configuration changes, and planned extensions.

Original project:

`https://github.com/krishnaik06/Kidney-Disease-Classification-Deep-Learning-Project`

Please refer to the repository's `LICENSE` file for licensing information.

---

## Author

**Kanak**

GitHub:
`https://github.com/Kanak3064`

Project Repository:
`https://github.com/Kanak3064/kidney-disease-classification-Platform`

---

## License

This project is distributed under the license included in the repository.

See [`LICENSE`](LICENSE) for details.
