# How do I install a library permanently in Google Colab?

This guide explains how to install Python libraries in Google Colab so they persist across sessions (by using Google Drive), and includes tips for connecting Colab to a local Jupyter server.

---

## Table of contents

1. [Installing a Library Permanently in Colab](#installing-a-library-permanently-in-colab)
2. [Connecting Colab to a Local Jupyter Server (Advanced)](#connecting-colab-to-a-local-jupyter-server-advanced)
3. [Troubleshooting](#troubleshooting)
4. [Credits](#credits)

---

## Installing a library permanently in Colab

Google Colab resets its environment every time you restart, so any installed library is lost. However, you can "permanently" install libraries by saving them to your Google Drive.

### Step-by-step instructions

#### 1. Mount Google Drive

```python
from google.colab import drive
drive.mount('/content/drive')
```
> This command connects your Google Drive to Colab at `/content/drive`.

#### 2. Set the installation path

Decide where you want to store your libraries in Drive. For example:

```python
import sys
nb_path = '/content/drive/MyDrive/Colab Notebooks/MyModules'
```
> Here, we’ll save libraries to a folder called `MyModules` in your Colab Notebooks.

#### 3. Install the library to Google Drive

Replace `jdc` with any library you want to install:

```python
!pip install --target=$nb_path jdc
```

#### 4. Add the path to sys.path

This step lets Python find your installed library:

```python
if nb_path not in sys.path:
    sys.path.append(nb_path)
```

#### 5. Import and use your library

```python
import jdc
```

**Tip:**  
Repeat steps 2, 4, and 5 in every new Colab notebook after mounting Google Drive.  
You only need to run step 3 (install) once per library, unless you want to upgrade it.

---

## Connecting Colab to a local jupyter server (Advanced)

Sometimes, you may want to run Colab notebooks on your own computer using your local resources.

### Requirements

- Jupyter is installed on your local machine.
- You know your local machine’s IP address.

### Step-by-step

1. **Install jupyter (if not already installed):**
    ```bash
    pip3 install jupyterlab
    ```

2. **Start jupyter notebook:**
    ```bash
    jupyter notebook --NotebookApp.allow_origin='https://colab.research.google.com' --port=8888 --NotebookApp.port_retries=0
    ```

3. **Copy the access token** from your terminal output.

4. **In Google Colab:**  
   Go to `File` > `Connect to local runtime…` and paste the URL from step 3.

> **Note:** This process is more advanced and can have security implications. Only use this if you understand what it does.

---

## Troubleshooting

- **Drive not mounting?**  
  Make sure you are logged into the correct Google account.
- **Permission errors?**  
  Check if you have write access to the target folder in Drive.
- **Library not found after restarting Colab?**  
  Ensure you’ve appended the correct path to `sys.path` and that the library exists in your Drive folder.

---

## Credits

UY1 Néo Quanticiens – Espace Documents, Trucs et Astuces

---
