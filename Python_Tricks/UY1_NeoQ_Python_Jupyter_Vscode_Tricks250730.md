# Installing Python via Miniforge (with mamba) on Linux

[![Miniforge](https://github.com/conda-forge/miniforge/actions/workflows/ci.yml/badge.svg)](https://github.com/conda-forge/miniforge/actions/workflows/ci.yml)
[![GitHub downloads](https://img.shields.io/github/downloads/conda-forge/miniforge/total.svg)](https://tooomm.github.io/github-release-stats/?username=conda-forge&repository=miniforge)

**Note:**
- **Miniforge** is like miniconda, but uses the conda-forge channel by default.
- **mamba** is a fast drop-in replacement for conda, included by default in Miniforge. It performs parallel downloads and can reuse packages already downloaded in other environments.

---

## Table of Contents

1. [Install Miniforge](#install-miniforge)
2. [Install Main Packages](#install-main-packages)
3. [JupyterLab KaTeX Extension](#jupyterlab-katex-extension)
4. [Environment Management](#environment-management)
5. [Adding Jupyter Kernels](#adding-jupyter-kernels)
6. [Changing Jupyter Working Directory](#changing-jupyter-working-directory)
7. [Creating a Jupyter Desktop Shortcut](#creating-a-jupyter-desktop-shortcut)
8. [Visual Studio Code (VS Code) Setup](#visual-studio-code-vs-code-setup)
9. [Free AI Coding Assistants (JupyterLab & VS Code)](#free-ai-coding-assistants-jupyterlab--vs-code)

---

## Install Miniforge

1. **Download the installer (~64 MB):**
    ```sh
    wget -c https://github.com/conda-forge/miniforge/releases/latest/download/Miniforge3-Linux-x86_64.sh
    ```
2. **Install:**
    ```sh
    bash Miniforge3-Linux-x86_64.sh
    ```
    - Accept the license terms and follow the prompts.
    - At the end, close and reopen your terminal. You should see `(base)` in your prompt.

3. **Update mamba and conda:**
    ```sh
    mamba update mamba conda -y
    ```

---

## Install Main Packages

With the base environment active, install the most up-to-date recommended packages for Python, Jupyter, and data science:

```sh
mamba install jupyterlab notebook ipykernel nb_conda_kernels jupyterlab_widgets jupyterlab-git numpy pandas scipy matplotlib seaborn scikit-learn statsmodels plotly bokeh altair ipywidgets jupyterlab-geojson jupyterlab-drawio jupyterlab-matplotlib jupyterlab-katex jupytext tqdm joblib memory_profiler line_profiler -y
```

**Optional deep learning packages:**  
If you need machine learning/deep learning:
```sh
mamba install tensorflow pytorch xgboost lightgbm -y
```

---

## JupyterLab KaTeX Extension

```sh
pip install jupyterlab-katex
```
- KaTeX is a faster alternative to MathJax for rendering LaTeX math in JupyterLab. If equations are not rendered correctly, you may want to switch back to MathJax.

---

## Environment Management

### Create a new environment

```sh
mamba create -n myenv python=3.11 -y
```
Replace `myenv` and `3.11` as desired.

### List environments

```sh
mamba info --envs
# or
mamba env list
```

### Activate/deactivate an environment

```sh
mamba activate myenv
# ...
mamba deactivate
```

---

## Adding Jupyter Kernels

To use your environments as Jupyter kernels:

1. **Install kernel tools (if not already):**
    ```sh
    mamba install ipykernel nb_conda_kernels -y
    ```

2. **Register each environment as a kernel:**
    ```sh
    python -m ipykernel install --user --name myenv
    ```
    Replace `myenv` with your environment’s name.  
    Run this in each environment you want to appear in Jupyter.

3. **List available kernels:**
    ```sh
    jupyter kernelspec list
    ```

---

## Changing Jupyter Working Directory

1. **Generate config file:**
    ```sh
    jupyter notebook --generate-config
    ```
    Config file: `~/.jupyter/jupyter_notebook_config.py`

2. **Edit the config:**
    - Find the line: `# c.NotebookApp.notebook_dir = ''`
    - Uncomment and set your desired path:
        ```python
        c.NotebookApp.notebook_dir = '/path/to/your/folder'
        ```

**For JupyterLab:**
- Generate config: `jupyter lab --generate-config`
- Edit `~/.jupyter/jupyter_lab_config.py` and set:
    ```python
    c.ServerApp.root_dir = '/path/to/your/folder'
    ```

---

## Creating a Jupyter Desktop Shortcut

1. **Create a file named `JupyterLab.desktop` on your desktop.**
2. **Paste the following content:**
    ```ini
    [Desktop Entry]
    Encoding=UTF-8
    Name=JupyterLab
    GenericName=JupyterLab
    Comment=Start Jupyter Lab server
    Exec=gnome-terminal --tab -- /bin/bash -c "~/miniforge3/bin/jupyter-lab;bash"
    Icon=jupyter-lab
    Type=Application
    Categories=Development;
    StartupNotify=true
    StartupWMClass=jupyter-lab
    Actions=open-browser

    [Desktop Action open-browser]
    Name=Open in browser
    Exec=xdg-open http://localhost:8888/lab
    ```
3. **For Jupyter Notebook, use similar content but replace `jupyter-lab` with `jupyter-notebook`.**

4. **Alternatively, search for “Jupyter” in your software manager and install the launcher directly.**

---

## Visual Studio Code (VS Code) Setup

VS Code is a modern, free, cross-platform code editor ideal for Python, Jupyter, and data science workflows.

### Recommended Extensions

- **Python** (Microsoft):  
  Essential for Python support, linting, debugging, and code navigation.

- **Jupyter** (Microsoft):  
  Native support for Jupyter notebooks (`.ipynb`), interactive cells, and variable explorer.

- **Pylance** (Microsoft):  
  Fast, feature-rich language server for Python with rich auto-completions and type checking.

- **Jupyter Keymap** (Microsoft):  
  Jupyter-style keyboard shortcuts in VS Code.

- **Jupyter Notebook Renderers** (Microsoft):  
  Enhanced, rich output rendering for Jupyter notebooks.

- **GitLens** (GitKraken):  
  Powerful Git integration for viewing code history and collaboration.

- **Markdown All in One** (Yu Zhang):  
  Improved Markdown editing, preview, and table of contents.

- **Code Spell Checker** (Street Side Software):  
  Spell checking for source code and markdown.

#### Additional Useful Extensions

- **Black Formatter** or **autopep8**:  
  Automatic code formatting.

- **isort**:  
  Automatically sorts Python imports.

- **Rainbow CSV**:  
  Colorful CSV/TSV viewing and editing.

- **TabNine**:  
  AI-powered code completion (free tier available).

---

### Tips

- Use the VS Code integrated terminal to activate your conda/mamba environment before running or debugging code.
- Open Jupyter notebooks directly in VS Code for a rich, interactive experience.
- Use the variable explorer and interactive plots when working with data.

---

## Free AI Coding Assistants (JupyterLab & VS Code)

### Codeium (Free, Powerful AI Coding Assistant)

**For JupyterLab:**
- **Install:**  
  ```sh
  pip install codeium-jupyter
  ```
- **Features:**  
  Free completion, suggestions, and code explanations in JupyterLab and notebooks. You may need a (free) Codeium account.

**For VS Code:**
- **Install:**  
  Search for "Codeium" in the Extensions Marketplace or [install here](https://marketplace.visualstudio.com/items?itemName=Codeium.codeium).
- **Features:**  
  Free for individuals, offers AI completions, inline suggestions, and chat.

---

### Gemini (Google AI)

**For VS Code:**
- **Install:**  
  Search for "Gemini" in the Extensions Marketplace or check [Google's official Gemini for VS Code](https://workspace.google.com/marketplace/app/gemini_for_vscode/).
- **Features:**  
  Gemini provides AI code assistance and chat (may require a Google account and region availability).  
  As of 2025, Gemini is not natively available for JupyterLab; you can use its API in your Python code or through custom VS Code integration.

---

### Other Free AI Tools

- **TabNine:**  
  Free tier available for both JupyterLab (via plugin) and VS Code.

- **Continue:**  
  Open-source, local-first AI coding assistant for VS Code, can connect to your own models (including Gemini API, OpenAI, etc.).

---

**For more details, see the [Miniforge documentation](https://github.com/conda-forge/miniforge) and [VS Code Python documentation](https://code.visualstudio.com/docs/languages/python).**
