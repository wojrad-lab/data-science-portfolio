# 0002-universal-jupyter-notebook-template

**Universal Jupyter Notebook Template**

**Description:** Professional starting template for every Jupyter Notebook (.ipynb) in this project.
Use this at the top of every new notebook (course exercises, portfolio projects).

**Author:** wojrad-lab  
**Date:** 2026-05-10  
**Version:** 1.0

## First cell (Markdown) - copy this as the very first cell

# Notebook Title

**Description:** Short description of what this notebook does  
**Author:** wojrad-lab  
**Date:** 2026-05-10  
**Version:** 1.0

**Notes:**
- Run in Jupyter / VS Code Notebook
- All paths are relative to the project root

## Second cell (Code) - always run this first

```python
# ====================== STANDARD JUPYTER SETUP ======================
%matplotlib inline
%load_ext autoreload
%autoreload 2

# ====================== IMPORTS ======================
# Standard library

import sys
import os

# Third-party libraries (add as needed from the course)
# import numpy as np
# import pandas as pd
# import matplotlib.pyplot as plt
# import seaborn as sns

# ====================== PROJECT PATH CONFIG ======================
# Set project root so paths work no matter where you run the notebook
from pathlib import Path
PROJECT_ROOT = Path.cwd().parent.parent  # adjust if needed
sys.path.append(str(PROJECT_ROOT))

print("✅ Notebook started successfully")
print(f"Project root: {PROJECT_ROOT}")
```