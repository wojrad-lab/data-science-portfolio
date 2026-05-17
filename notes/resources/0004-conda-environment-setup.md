# Note: Creating Conda Environment for Data Science (ds-bootcamp)

**Date:** May 17, 2026  
**Goal:** Full understanding from zero of everything that happened while creating the `ds-bootcamp` environment with Python 3.13.9 + DS stack (pandas, numpy, matplotlib, seaborn, jupyterlab).  
**Level:** Zero gaps – everything explained simply, step by step.

---

## 1. What is Conda? (basics from zero)

**Conda** is a **package and environment manager**.

- **Why do we use it?**
  - Python has many libraries (pandas, numpy, scikit-learn, etc.).
  - Different projects need different versions of these libraries.
  - Without Conda you install everything globally → version conflicts appear very quickly (e.g. one project needs pandas 2.0, another needs 1.5).
  - **Conda solves this** by creating **isolated environments** – each environment has its own Python and its own libraries.

**Basic concepts:**
- **base** – the default Conda environment (where you installed Miniconda/Anaconda).
- **ds-bootcamp** – our dedicated environment for the Data Science project.
- **kernel** – the "engine" of Python that Jupyter uses to run code.

---

## 2. What exactly did we do? (chronological order)

### Step 1: Check current state (base)

```bash
python --version          # Shows Python version in the active environment
conda --version           # Conda version
jupyter --version         # Checks if Jupyter is installed
which python              # Full path to the Python interpreter
echo $CONDA_DEFAULT_ENV   # Name of the active environment (base)
```

**Result:** You had Python 3.13.9 in `base` + Jupyter Lab 4.4.7.

### Step 2: Create environment with Python 3.11 (first attempt)

```bash
conda create -n ds-bootcamp python=3.11 -y
conda activate ds-bootcamp
conda install jupyterlab pandas numpy matplotlib seaborn -y
```

**What do these commands do?**
- `conda create -n ds-bootcamp python=3.11 -y`  
  → Creates a new, empty environment named `ds-bootcamp` with Python version 3.11.  
  The `-y` flag = automatically answers "yes" to all questions.
- `conda activate ds-bootcamp`  
  → Switches the terminal to the new environment (prompt changes to `(ds-bootcamp)`).
- `conda install ... -y`  
  → Installs the selected DS packages in this environment.

**Why did we change to 3.13 later?**  
You wanted the newest stable Python version (3.13.9), which is fully supported in 2026 by all DS libraries.

### Step 3: Remove old environment and create new one with Python 3.13

```bash
conda deactivate                    # Exit ds-bootcamp back to base
conda env remove -n ds-bootcamp -y  # Completely remove the old environment
conda create -n ds-bootcamp python=3.13 -c conda-forge -y
conda activate ds-bootcamp
conda install jupyterlab pandas numpy matplotlib seaborn scikit-learn -c conda-forge -y
```

**Key differences:**
- `-c conda-forge` = we use the **conda-forge** channel (better support for Python 3.13 and newer package versions).
- We added `scikit-learn` (will be useful later for ML).

### Step 4: Register kernel for Jupyter

```bash
python -m ipykernel install --user --name ds-bootcamp --display-name "Python (ds-bootcamp)"
```

**What does this do?**  
Registers our environment as a separate kernel in Jupyter. Thanks to this, in Jupyter Lab you can select exactly this environment (Python 3.13 + all installed libraries).

### Step 5: Testing

```python
import sys
print(sys.executable)   # Full path to Python (should be .../ds-bootcamp/bin/python)
print(sys.version)      # 3.13.x
import pandas as pd
import numpy as np
print("Pandas:", pd.__version__)
print("NumPy:", np.__version__)
print("Environment works correctly!")
```

---

## 3. Basic Conda Commands (cheat sheet with explanations)

| Command | Syntax | What it does | Example |
|---------|--------|--------------|---------|
| **create** | `conda create -n NAME python=VERSION -y` | Creates a new environment | `conda create -n ds-bootcamp python=3.13 -y` |
| **activate** | `conda activate NAME` | Enters the environment | `conda activate ds-bootcamp` |
| **deactivate** | `conda deactivate` | Exits to the previous environment (usually base) | `conda deactivate` |
| **install** | `conda install package1 package2 -y` | Installs packages in the active environment | `conda install pandas numpy -y` |
| **list** | `conda list` | Shows all installed packages | `conda list` |
| **list envs** | `conda env list` | Shows all environments | `conda env list` |
| **remove env** | `conda env remove -n NAME -y` | Removes the entire environment | `conda env remove -n ds-bootcamp -y` |
| **update** | `conda update -n base conda -y` | Updates Conda itself | `conda update -n base conda -y` |
| **search** | `conda search package` | Searches for a package in channels | `conda search pandas` |

**Useful extra flags:**
- `-y` or `--yes` → automatic "yes" answer
- `-c channel` → specifies the channel (e.g. `-c conda-forge`)
- `--name NAME` or `-n NAME` → environment name

---

## 4. How to select the environment in tools?

### In Jupyter Lab
1. Run `jupyter lab`
2. In the top-right corner of the notebook click on the kernel name
3. Select **"Python (ds-bootcamp)"**

### In VS Code
1. `Ctrl + Shift + P` → type **"Python: Select Interpreter"**
2. Select the path containing `ds-bootcamp` (e.g. `/home/radek/.conda/envs/ds-bootcamp/bin/python`)

---

## 5. Summary – what did we gain?

- **Isolated environment** `ds-bootcamp` with Python **3.13.9**
- Installed: `jupyterlab`, `pandas`, `numpy`, `matplotlib`, `seaborn`, `scikit-learn`
- Full version control – nothing breaks the system
- Easy switching between projects (each project = separate environment)
- Ready for learning Data Science from scratch
*Note prepared by Grok – mentor of your Data Science project*  
*wojrad-lab / May 17, 2026*
