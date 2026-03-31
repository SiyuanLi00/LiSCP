
# Lightweight Stylistic Consistency Profiling: Robust Detection of LLM-Generated Textual Content for Multimedia Moderation

This repository contains the code for a robust method for detecting machine-generated texts by leveraging stylistic consistency analysis. The approach combines discrete stylistic indicators and continuous representations to detect machine-generated content across multiple domains. 

## Framework Overview

The method constructs **stylistic consistency profiles**, which capture the stability of text across adversarial perturbations, ensuring robustness against manipulations such as paraphrasing or hybrid human–AI authorship.

![Framework Pipeline](figure-pipeline.svg)

*The pipeline models both discrete and continuous stylistic representations to ensure robust text authenticity detection.*

## Installation

### Prerequisites

- Python 3.9 or higher
- CUDA-compatible GPU (recommended for optimal performance)

### Setup

1. Clone the repository:
```bash
git clone https://github.com/xxx.git
cd xxx
```

2. Create a virtual environment:
```bash
conda create -n xxx python=3.9
conda activate xxx
```

3. Install dependencies:
```bash
pip install -r requirements.txt
```

## Dataset

The framework is evaluated across multiple domains to test its robustness in real-world scenarios. It requires datasets in JSON format with the following structure:

### Data Format
```json
[
    {
        "Index": 1,
        "Text": "Your text content here...",
        "Source": "human (or GPT for machine-generated)"
    }
]
```

### Supported Domains
- **Reuter News**: Human-written texts from Reuters_50_50 dataset (2006)
- **Student Essays**: Academic writing samples from IvyPanda repository
- **HumanEval Code**: Programming code snippets from HumanEval dataset
- **Yelp Reviews**: Restaurant and business reviews from Yelp
- **Paper Abstracts**: 500 abstracts sampled from ACL 2023 papers

The framework also includes the **RAID dataset** for evaluating adversarial robustness:

- **RAID Dataset**: The largest benchmark for AI-generated text detection, including texts from 11 LLMs, 4 decoding strategies, and 12 adversarial attacks.

## Quick Start

### Basic Usage
To extract style features and evaluate the robustness of your model, run the following steps:

1. Configure your settings in `main.py` (openai API key, dataset paths, and feature vectors).
2. Run `main.py` to extract stylistic features from your dataset:
```bash
python main.py
```

3. After generating the feature vectors, run `experiment_main.py` to perform text classification:
```bash
python experiment_main.py
```

## Experiments

The framework is designed to evaluate its robustness and explainability under various settings:

### Out-of-Domain Experiment
To evaluate the model’s performance across domains, run the following:
```bash
python experiment_OOD.py
```

### Robustness Experiment
For testing the adversarial robustness, use the scripts in the `robust_dataset_building/` directory to prepare and evaluate robustness datasets:
```bash
python robust_dataset_building/experiment.py
```

## Citation
If you use this code in your research, please cite our paper.
