# 📦 Install Python Libraries Permanently in Google Colab

> Google Colab resets its environment every session, but you can persist libraries by storing them in Google Drive!

---

## Table of Contents

1. [Why This Matters](#why-this-matters)
2. [Install Libraries to Google Drive](#install-libraries-to-google-drive)
3. [Using Your Persistent Libraries](#using-your-persistent-libraries)
4. [Advanced: Connect to Local Runtime](#advanced-connect-to-local-runtime)
5. [Troubleshooting](#troubleshooting)

---

## Why This Matters

| Problem | Solution |
|---------|----------|
| ❌ Colab resets after each session | ✅ Store libraries in Google Drive |
| ❌ Reinstall packages every time | ✅ Install once, use forever |
| ❌ Slow setup for each notebook | ✅ Quick import after mounting Drive |

---

## Install Libraries to Google Drive

### Step 1: Mount Google Drive

```python
from google.colab import drive
drive.mount('/content/drive')
```

> 🔗 This connects your Google Drive to Colab at `/content/drive`.

---

### Step 2: Set Installation Path

```python
import sys
LIB_PATH = '/content/drive/MyDrive/Colab Libraries'
```

> 📁 You can customize this path. Make sure the folder exists!

---

### Step 3: Install Library to Drive

Replace `jdc` with any library you need:

```python
!pip install --target=$LIB_PATH jdc
```

> ⏱️ **Note**: This may take a few minutes depending on the library size.

---

### Step 4: Add Path to `sys.path`

```python
if LIB_PATH not in sys.path:
    sys.path.append(LIB_PATH)
```

> 🐍 This tells Python where to find your installed libraries.

---

### Step 5: Import and Use

```python
import jdc
# Use the library as normal!
```

---

## Using Your Persistent Libraries

### In New Colab Sessions

After mounting Drive, you only need to run **Steps 2, 4, and 5**:

```python
# Quick setup for new sessions
from google.colab import drive
drive.mount('/content/drive')

import sys
LIB_PATH = '/content/drive/MyDrive/Colab Libraries'

if LIB_PATH not in sys.path:
    sys.path.append(LIB_PATH)

# Now import your libraries!
import jdc
```

### Install Multiple Libraries

```python
# Install several at once
!pip install --target=$LIB_PATH pandas numpy matplotlib seaborn
```

### Upgrade a Library

```python
!pip install --upgrade --target=$LIB_PATH jdc
```

---

## Advanced: Connect to Local Runtime

> ⚠️ **Advanced users only** – Run Colab notebooks on your local machine!

### Requirements

- Jupyter installed locally
- Known local IP address
- Understanding of security implications

### Step 1: Install Jupyter (if needed)

```bash
pip3 install jupyterlab
```

---

### Step 2: Start Jupyter with Colab Access

```bash
jupyter notebook \
  --NotebookApp.allow_origin='https://colab.research.google.com' \
  --port=8888 \
  --NotebookApp.port_retries=0
```

---

### Step 3: Connect from Colab

1. Copy the access URL from terminal output
2. In Colab: **File** → **Connect to local runtime...**
3. Paste the URL

> 🔒 **Security Warning**: Only use this on trusted networks!

---

## Troubleshooting

| Issue | Solution |
|-------|----------|
| **Drive won't mount** | Ensure you're logged into the correct Google account |
| **Permission errors** | Check write access to the target folder in Drive |
| **Library not found** | Verify `sys.path` includes your library path |
| **Import errors** | Restart the runtime after installation |
| **Slow installation** | Some libraries have many dependencies—be patient! |

### Quick Debug Commands

```python
# Check if library is installed
!ls $LIB_PATH

# Verify Python can see the path
import sys
print(sys.path)

# Check installed packages
!pip list --path=$LIB_PATH
```

---

## 💡 Pro Tips

1. **Organize by project**: Create separate folders for different projects
   ```python
   LIB_PATH = '/content/drive/MyDrive/Colab Libraries/ML-Project'
   ```

2. **Export requirements**: Save your library list
   ```python
   !pip freeze --path=$LIB_PATH > requirements.txt
   ```

3. **Use a startup script**: Create a snippet to run automatically

---

*UY1 Néo Quanticiens – Python Tricks Collection*
