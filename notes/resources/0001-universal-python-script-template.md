# 0001-universal-python-script-template

**Universal Python Script Template**

**Description:** Professional starting template for every Python script in this project.  
Use this every time you create a new `.py` file (course exercises, portfolio projects, personal scripts).

**Author:** wojrad-lab  
**Date:** 2026-05-10  
**Version:** 1.0

## The Template (copy-paste this)

```python
#!/usr/bin/env python3
# -*- coding: utf-8 -*-

"""
Script name: filename.py
Description: Short description of what this script does
Author: wojrad-lab
Date: 2026-05-10
Version: 1.0
"""

# ====================== IMPORTS ======================
# Standard library first
import sys      # Gives access to command-line arguments, Python version, system paths, etc.
                # Very useful later when you want to run script with parameters
                # or check Python environment.

import os       # Allows interaction with the operating system:
                # - creating/deleting folders and files
                # - checking if a file exists
                # - getting environment variables
                # - working with paths in a cross-platform way

# Then third-party libraries (add when needed)
# import pandas as pd

# Then your own modules (later)


# ====================== CONSTANTS & CONFIG ======================


# ====================== FUNCTIONS ======================


# ====================== MAIN CODE ======================
if __name__ == "__main__":
    print("Script started successfully!")
    
    # ←←← YOUR CODE GOES HERE ←←←
    
    print("End of script.")
```