# Environment Setup Guide - Rebar Detection Jupyter Notebook

This guide provides step-by-step instructions for setting up the Python environment required to run the **Rebar Detection** Jupyter notebook (`Rebar20251022_filtered.ipynb`).

## 📋 System Requirements

- **Operating System**: Windows, macOS, or Linux
- **Python Version**: 3.9.x (tested with Python 3.9.25)
- **RAM**: Minimum 8 GB (16 GB recommended for large point clouds)
- **Storage**: At least 2 GB free space for dependencies and data

## 🔧 Installation Methods

Choose one of the following methods to set up your environment:

### Method 1: Using Conda (Recommended)

Conda provides better dependency management and is recommended for scientific computing.

#### Step 1: Install Anaconda or Miniconda

Download and install from:
- **Anaconda**: https://www.anaconda.com/download
- **Miniconda** (lightweight): https://docs.conda.io/en/latest/miniconda.html

#### Step 2: Create a New Conda Environment

```bash
# Create environment with Python 3.9
conda create -n rebar-detection python=3.9

# Activate the environment
conda activate rebar-detection
```

#### Step 3: Install Dependencies

```bash
# Install core scientific libraries
conda install -c conda-forge numpy scipy pandas matplotlib scikit-learn

# Install Open3D for point cloud processing
pip install open3d

# Install Excel export libraries
pip install openpyxl

# Install Jupyter
conda install jupyter jupyterlab
```

#### Step 4: Launch Jupyter

```bash
jupyter lab
# or
jupyter notebook
```

---

### Method 2: Using pip with Virtual Environment

This method uses Python's built-in venv for environment isolation.

#### Step 1: Verify Python Installation

```bash
# Check Python version (should be 3.9.x)
python --version
# or on some systems
python3 --version
```

If Python 3.9 is not installed, download it from https://www.python.org/downloads/

#### Step 2: Create Virtual Environment

**On Windows:**
```bash
# Create virtual environment
python -m venv rebar-env

# Activate environment
rebar-env\Scripts\activate
```

**On macOS/Linux:**
```bash
# Create virtual environment
python3 -m venv rebar-env

# Activate environment
source rebar-env/bin/activate
```

#### Step 3: Upgrade pip

```bash
python -m pip install --upgrade pip
```

#### Step 4: Install Dependencies

```bash
# Install all required packages
pip install numpy scipy pandas matplotlib scikit-learn open3d openpyxl jupyter jupyterlab
```

#### Step 5: Launch Jupyter

```bash
jupyter lab
# or
jupyter notebook
```

---

### Method 3: Using requirements.txt (Quick Setup)

Create a `requirements.txt` file with the following content:

```txt
# Core numerical and scientific libraries
numpy>=1.21.0,<1.24.0
scipy>=1.7.0
pandas>=1.3.0

# Point cloud processing
open3d>=0.13.0

# Machine learning
scikit-learn>=1.0.0

# Visualization
matplotlib>=3.4.0

# Excel export
openpyxl>=3.0.0

# Jupyter
jupyter>=1.0.0
jupyterlab>=3.0.0
```

Then install using:

```bash
# Create and activate virtual environment first (see Method 2, Steps 1-2)

# Install from requirements file
pip install -r requirements.txt
```

---

## 📦 Detailed Package Requirements

| Package | Minimum Version | Purpose |
|---------|----------------|---------|
| numpy | 1.21.0 | Array operations and numerical computing |
| scipy | 1.7.0 | Scientific computing (optimization, ODR) |
| pandas | 1.3.0 | Data manipulation and Excel export |
| matplotlib | 3.4.0 | Visualization and plotting |
| scikit-learn | 1.0.0 | Machine learning (DBSCAN clustering) |
| open3d | 0.13.0 | 3D point cloud processing and visualization |
| openpyxl | 3.0.0 | Excel file creation and formatting |
| jupyter | 1.0.0 | Jupyter Notebook interface |
| jupyterlab | 3.0.0 | JupyterLab interface (optional but recommended) |

**Note**: Built-in Python modules used (no installation needed):
- `time` - Performance timing
- `datetime` - Timestamp generation
- `json` - JSON file export
- `random` - Random sampling for RANSAC

---

## ✅ Verify Installation

After installation, verify that all packages are correctly installed:

### Using Python

```python
# Run this in a Python shell or Jupyter cell
import numpy as np
import scipy
import pandas as pd
import matplotlib.pyplot as plt
import sklearn
import open3d as o3d
import openpyxl
import json
import time
from datetime import datetime

print("All packages imported successfully!")
print(f"NumPy version: {np.__version__}")
print(f"SciPy version: {scipy.__version__}")
print(f"Pandas version: {pd.__version__}")
print(f"Matplotlib version: {plt.matplotlib.__version__}")
print(f"Scikit-learn version: {sklearn.__version__}")
print(f"Open3D version: {o3d.__version__}")
print(f"OpenPyXL version: {openpyxl.__version__}")
```

### Expected Output

```
All packages imported successfully!
NumPy version: 1.23.x
SciPy version: 1.9.x
Pandas version: 1.5.x
Matplotlib version: 3.6.x
Scikit-learn version: 1.1.x
Open3D version: 0.16.x
OpenPyXL version: 3.0.x
```

---

## 🚀 Running the Notebook

1. **Start Jupyter**:
   ```bash
   # Activate your environment first
   conda activate rebar-detection  # if using conda
   # or
   source rebar-env/bin/activate   # if using venv (macOS/Linux)
   
   # Launch Jupyter
   jupyter lab
   ```

2. **Open the notebook**:
   - Navigate to `Rebar20251022_filtered.ipynb` in the file browser
   - Click to open

3. **Prepare your data**:
   - Ensure your point cloud files (`.ply` format) are in the correct location
   - Update file paths in the notebook cells as needed

4. **Run the notebook**:
   - Run cells sequentially: `Shift + Enter`
   - Or run all cells: Menu → Run → Run All Cells

---

## 🔧 Troubleshooting

### Issue: ImportError for open3d

**Solution**:
```bash
pip install --upgrade open3d
```

If still failing on Windows, try:
```bash
pip install open3d-python
```

### Issue: "Microsoft Visual C++ is required" (Windows)

Open3D requires Visual C++ redistributables on Windows.

**Solution**: Download and install from:
https://visualstudio.microsoft.com/downloads/ (scroll to "Other Tools and Frameworks")

### Issue: Out of Memory

Large point clouds may require more RAM.

**Solution**:
- Process one point cloud at a time
- Reduce point cloud density before processing
- Adjust `DENSITY_PERCENTILE` parameter to retain fewer points
- Close other applications to free up memory

### Issue: Jupyter kernel dies

**Solution**:
```bash
# Reinstall ipykernel
pip install --upgrade ipykernel

# Register the kernel
python -m ipykernel install --user --name=rebar-detection
```

### Issue: Slow performance

**Solution**:
- Ensure you're using a local Jupyter server (not cloud-based)
- Check if your system has sufficient RAM
- Consider downsampling very large point clouds
- Use parameter tuning to reduce computational load

### Issue: openpyxl formatting errors

**Solution**:
```bash
pip install --upgrade openpyxl
```

---

## 📁 File Structure

Ensure your working directory has the following structure:

```
project_folder/
│
├── Rebar20251022_filtered.ipynb    # Main notebook
├── data/                            # Point cloud data folder
│   ├── PC1_Rotated.ply
│   └── PC2_Rotated.ply
│
├── outputs/                         # Output folder (created automatically)
│   ├── *.xlsx                       # Excel results
│   └── *.json                       # JSON geometry files
│
└── requirements.txt                 # (Optional) Package list
```

---

## 🌐 Platform-Specific Notes

### Windows
- Use Anaconda Prompt or Command Prompt
- File paths use backslashes: `C:\Users\...\data\`
- May require Visual C++ redistributables for Open3D

### macOS
- Use Terminal
- File paths use forward slashes: `/Users/.../data/`
- May need to install Xcode Command Line Tools:
  ```bash
  xcode-select --install
  ```

### Linux
- Use Terminal
- File paths use forward slashes: `/home/.../data/`
- Open3D should install without issues on most distributions

---

## 🔄 Updating Dependencies

To update all packages to their latest compatible versions:

**Using Conda:**
```bash
conda activate rebar-detection
conda update --all
```

**Using pip:**
```bash
pip install --upgrade numpy scipy pandas matplotlib scikit-learn open3d openpyxl jupyter jupyterlab
```

---

## 🐍 Alternative: Using Docker (Advanced)

For a completely isolated and reproducible environment:

### Dockerfile

```dockerfile
FROM python:3.9-slim

WORKDIR /app

# Install system dependencies
RUN apt-get update && apt-get install -y \
    libgl1-mesa-glx \
    libglib2.0-0 \
    && rm -rf /var/lib/apt/lists/*

# Copy requirements
COPY requirements.txt .

# Install Python packages
RUN pip install --no-cache-dir -r requirements.txt

# Expose Jupyter port
EXPOSE 8888

# Start Jupyter
CMD ["jupyter", "lab", "--ip=0.0.0.0", "--allow-root", "--no-browser"]
```

### Build and Run

```bash
# Build image
docker build -t rebar-detection .

# Run container
docker run -p 8888:8888 -v $(pwd):/app rebar-detection
```

---

## 📞 Support

If you encounter issues not covered in this guide:

1. **Check package documentation**:
   - Open3D: http://www.open3d.org/docs/
   - Scikit-learn: https://scikit-learn.org/stable/
   - SciPy: https://docs.scipy.org/doc/

2. **Verify Python version compatibility**:
   ```bash
   python --version
   ```

3. **Check installed package versions**:
   ```bash
   pip list
   # or
   conda list
   ```

4. **Create a fresh environment** if issues persist

---

## 📝 Quick Start Checklist

- [ ] Python 3.9.x installed
- [ ] Virtual environment created and activated
- [ ] All dependencies installed
- [ ] Import verification successful
- [ ] Jupyter Lab/Notebook running
- [ ] Point cloud data files prepared
- [ ] File paths updated in notebook
- [ ] Ready to run!

---

## 🎓 Additional Resources

- **Jupyter Notebook Tutorial**: https://jupyter-notebook.readthedocs.io/
- **Open3D Tutorial**: http://www.open3d.org/docs/latest/tutorial/
- **NumPy Quickstart**: https://numpy.org/doc/stable/user/quickstart.html
- **Pandas User Guide**: https://pandas.pydata.org/docs/user_guide/index.html

---

**Note**: This environment setup is specifically configured for the rebar detection pipeline. If you're working on multiple Python projects, consider using separate virtual environments for each to avoid package conflicts.

**Last Updated**: January 2025  
**Compatible with**: Python 3.9.x  
**Tested on**: Windows 10/11, macOS 12+, Ubuntu 20.04+
