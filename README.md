# User Behavior Prediction Model with DVC

This repository contains a machine learning pipeline for predicting user behavior using a **Random Forest Classifier**. The pipeline and dependencies are managed with **DVC (Data Version Control)**, ensuring reproducibility, version control, and easy tracking of dataset and model updates.

## Table of Contents
- [Overview](#overview)
- [Repository Structure](#repository-structure)
- [Installation](#installation)
- [Using DVC](#using-dvc)
- [Pipeline Stages](#pipeline-stages)
- [Running the Pipeline](#running-the-pipeline)
- [License](#license)

## Overview

The objective of this project is to train a classification model to predict user behavior. Using DVC, we can:
- Track changes to datasets and models.
- Define, manage, and execute the pipeline stages.
- Facilitate collaboration by ensuring consistency across different environments.

## Repository Structure

```plaintext
.
├── .dvc/                          # DVC configuration directory
├── .dvcignore                     # File specifying ignored files for DVC tracking
├── README.md                      # This README file
├── dvc.lock                       # Lock file tracking pipeline stages and dependencies
├── dvc.yaml                       # DVC pipeline configuration file
├── random_forest_model.joblib     # Trained Random Forest model
├── train.ipynb                    # Jupyter Notebook for model development and training
├── user_behavior_dataset.csv.dvc   # DVC file tracking the dataset
```

## Installation

### Prerequisites
- **Python 3.8+**
- **Git**
- **DVC**
- **Jupyter Notebook** (optional, for running notebooks)

### Install Dependencies
To install the required Python packages, run:

```bash
pip install -r requirements.txt
```

> **Note**: If DVC is not installed, use `pip install dvc` to add it to your environment.

## Using DVC

DVC helps manage the stages of this ML pipeline and ensures data and model versioning. Use the following basic DVC commands:
- `dvc add <file>`: Track a data file with DVC.
- `dvc repro`: Reproduce the pipeline.
- `dvc push`: Upload files to a remote storage.

## Pipeline Stages

### Defined Stages (in `dvc.yaml`)

1. **train_model**:
   - **Inputs**: `user_behavior_dataset.csv`, `train.py`
   - **Outputs**: `random_forest_model.joblib`
   - **Description**: Runs the training script `train.py` and outputs the trained model.

To view all pipeline stages visually, run:

```bash
dvc dag
```

## Running the Pipeline

To reproduce the pipeline and ensure all stages are up-to-date, use:

```bash
dvc repro
```

This command checks for any changes to the inputs, dependencies, or code and re-runs affected stages accordingly.
