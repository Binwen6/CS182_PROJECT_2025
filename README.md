# In-Context Learning with Mamba and Baselines

This repository contains code for experiments on in-context learning using Mamba and various baseline models. The codebase is organized for easy extension and reproducibility.

## Code Structure
```
.
├── simple_functions/
│ ├── imgs/ # Generated figures and plots
│ ├── models/ # Saved model checkpoints and experiment outputs
│ ├── src/ # Main source code for training, evaluation, and utilities
│ │ ├── conf/ # YAML configuration files for experiments
│ │ ├── train.py # Main training script
│ │ ├── eval.py # Evaluation script
│ │ ├── ... # Other utilities and model/task definitions
│ ├── requirements.txt # Python dependencies
│ ├── environment_default.yml # Conda environment (default)
│ ├── environment_droplet.yml # Conda environment (GPU/CUDA)
│ └── LICENSE
├── mamba_mod/ # Modified Mamba implementation (installable as a package)
│ ├── mamba_mod/ # Source code for the Mamba model
│ ├── setup.py
│ └── README.md
└── init.py
```

## Installation

1. **Clone the repository:**
   ```bash
   git clone <repo_url>
   cd <repo_root>
   ```

2. **Set up the Python environment:**
   - Using Conda (recommended):
     ```bash
     conda env create -f simple_functions/environment_default.yml
     conda activate in-context-learning
     ```
   - Or install dependencies via pip:
     ```bash
     pip install -r simple_functions/requirements.txt
     ```

3. **Install the modified Mamba module:**
   ```bash
   cd mamba_mod
   pip install -e .
   cd ..
   ```

## Usage

### Training

To train a model, run the training script with a configuration file. For example:
```bash
cd simple_functions/src
python train.py --config conf/gaussian_kernel_regression_mamba.yaml --training.seed 1
```
- Configuration files for different tasks and models are in `simple_functions/src/conf/`.

### Batch Experiments

You can run multiple experiments using the provided shell script:
```bash
bash simple_functions/src/experiments.sh
```

### Evaluation

To evaluate a trained model, use:
```bash
python eval.py <run_dir> <run_id> <n_test_points>
```
- Replace `<run_dir>`, `<run_id>`, and `<n_test_points>` as needed.

## Reproduction Guide

1. **Prepare the environment** as described above.
2. **Run training** for your desired configuration(s).
3. **Evaluate** the results using the evaluation script.
4. **Plots and figures** will be saved in `simple_functions/imgs/`.

## Notes

- Large model files and experiment outputs are ignored by git (see `.gitignore`).
- For more details on the Mamba implementation, see `mamba_mod/README.md`.

---

**License:** See `simple_functions/LICENSE` for details.