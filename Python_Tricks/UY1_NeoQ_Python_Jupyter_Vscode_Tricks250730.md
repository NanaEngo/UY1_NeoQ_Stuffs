# 🐍 Python Development Setup: Miniforge, JupyterLab & VS Code

[![Miniforge CI](https://img.shields.io/github/actions/workflow/status/conda-forge/miniforge/ci.yml?label=Miniforge%20Build)](https://github.com/conda-forge/miniforge/actions)
[![Total Downloads](https://img.shields.io/github/downloads/conda-forge/miniforge/total?color=blue&label=GitHub%20Downloads)](https://tooomm.github.io/github-release-stats/?username=conda-forge&repository=miniforge)
[![Conda-Forge](https://img.shields.io/conda/dn/conda-forge/conda?label=Conda-Forge%20Packages)](https://conda-forge.org/)

> **Key Advantages**
> - ✅ **Miniforge**: Miniconda alternative using **conda-forge** as default channel
> - ⚡ **mamba**: Blazing-fast conda replacement with parallel downloads
> - 📦 **Pre-configured**: Optimized for scientific Python workflows
> - 🌐 **Community-driven**: Managed by conda-forge community

> 💡 **For Beginners**: This guide helps you set up a professional Python environment for data science and machine learning. Miniforge is like a "Python ecosystem manager" that handles packages and dependencies for you.

---

## Table of Contents

1. [Install Miniforge](#-install-miniforge)
2. [Core Package Installation](#-core-package-installation)
3. [JupyterLab Enhancements](#-jupyterlab-enhancements)
4. [Environment Management](#-environment-management)
5. [Updating Packages](#-updating-packages)
6. [Jupyter Kernel Setup](#-jupyter-kernel-setup)
7. [Working Directory Configuration](#-working-directory-configuration)
8. [Desktop Integration](#-desktop-integration)
9. [VS Code Setup](#-vs-code-setup)
10. [AI Coding Assistants](#-ai-coding-assistants)
11. [Troubleshooting](#-troubleshooting)
12. [Resources](#-resources)

---

## 🚀 Install Miniforge

> 💡 **Beginner Explanation**: Miniforge installs Python and essential tools. Think of it as installing an "app store" for Python packages.

### Step 1: Download Installer

```bash
wget https://github.com/conda-forge/miniforge/releases/latest/download/Miniforge3-$(uname)-$(uname -m).sh
```

---

### Step 2: Run Installation

```bash
bash Miniforge3-$(uname)-$(uname -m).sh
```

- ✅ Accept license terms
- 📁 Choose installation location (default: `~/miniforge3`)
- ✅ Initialize conda when prompted (say "yes")

> 💡 **Why initialize?** This adds Miniforge to your system PATH so you can use it from any terminal.

---

### Step 3: Initialize & Update

```bash
# Load Miniforge settings into your current terminal
source ~/.bashrc  # or source ~/.zshrc if using Zsh

# Update all installed packages
mamba update --all -y
```

> 💡 **Pro Tip**: Add this to your `.bashrc`/`.zshrc` for auto-activation:
> ```bash
> echo "mamba activate" >> ~/.bashrc
> ```

---

## 📦 Core Package Installation

> 💡 **Beginner Explanation**: These are essential tools for data science. JupyterLab is like a web-based "Python workspace," while NumPy/Pandas are for data manipulation.

### Essential Data Science Stack

```bash
mamba install -c conda-forge \
  jupyterlab \            # Interactive coding environment
  jupyterlab-git \        # Git version control in Jupyter
  jupyterlab-widgets \    # Interactive controls
  numpy pandas scipy \    # Data manipulation libraries
  matplotlib seaborn plotly \  # Visualization tools
  scikit-learn statsmodels \   # Machine learning
  ipykernel nb_conda_kernels \ # Environment management
  jupytext tqdm \         # Notebook utilities
  black isort ruff \      # Code formatters
  -y
```

---

### Optional Extras

#### Machine Learning Libraries
```bash
mamba install -c conda-forge \
  tensorflow pytorch \      # Deep learning frameworks
  xgboost lightgbm catboost \  # Gradient boosting libraries
  -y
```

#### Performance Tools
```bash
mamba install -c conda-forge \
  numba dask \              # Speed up computations
  memory_profiler line_profiler \  # Check performance
  -y
```

> 💡 **Package Tips**:
> - Start with essential packages first
> - Add ML packages only if needed
> - `-y` flag automatically confirms installation

---

## ✨ JupyterLab Enhancements

> 💡 **Beginner Explanation**: These add-ons make JupyterLab more powerful—like installing extensions in a web browser.

### Essential Extensions

```bash
# LaTeX math rendering (for equations)
mamba install -c conda-forge jupyterlab-katex

# Diagramming tool integration
mamba install -c conda-forge jupyterlab-drawio

# Table of Contents generator
jupyter labextension install @jupyterlab/toc
```

### Activate Extensions

```bash
jupyter lab build
```

> 💡 **LaTeX Note**: For full document rendering (PDF export):
> ```bash
> sudo apt install texlive-full  # Debian/Ubuntu
> ```

---

## 🌱 Environment Management

> 💡 **Beginner Explanation**: Environments are like "separate workspaces" for different projects. This prevents package conflicts.

### Create New Environment

```bash
# Creates environment named "ds-env" with Python 3.12
mamba create -n ds-env python=3.12 -y
```

---

### Environment Operations

| Command | Description |
|---------|-------------|
| `mamba env list` | Shows all environments |
| `mamba activate ds-env` | Enters the environment |
| `mamba deactivate` | Exits current environment |
| `mamba env remove -n ds-env` | Deletes an environment |
| `mamba env export > environment.yml` | Saves environment configuration |

---

### Clone Environment

```bash
# Creates a backup copy of your base environment
mamba create --clone base --name base-backup
```

> 💡 **Environment Tips**:
> - Use different environments for different projects
> - Export `environment.yml` to share your setup
> - Keep base environment minimal

---

## 🔄 Updating Packages

> 💡 **Beginner Explanation**: Regularly updating packages gives you bug fixes, security patches, and new features. Think of it like updating apps on your phone!

### Update All Packages

```bash
mamba activate my-environment
mamba update --all -y
```

### Update a Specific Package

```bash
mamba update package-name -y
# Example: mamba update numpy -y
```

### Update to a Specific Version

```bash
mamba install package-name=version -y
# Example: mamba install pandas=2.1.0 -y
```

### Update Mamba Itself

```bash
mamba activate base
mamba update mamba conda -y
```

---

### Best Practices

1. **Update regularly**: Check for updates monthly
2. **Create backups**: Clone environments before major updates
   ```bash
   mamba create --clone my-env --name my-env-backup
   ```
3. **Test after updating**: Verify your code still works
4. **Pin critical packages**: For production, specify versions
   ```yaml
   # environment.yml
   dependencies:
     - python=3.12
     - numpy=1.26.0
     - pandas=2.1.0
   ```

### Checking for Updates

```bash
# See available updates without installing
mamba update --all --dry-run

# List outdated packages
mamba outdated
```

> ⚠️ **Warning**: Major updates (like Python version changes) might break code. Test thoroughly!

---

## ⚙️ Jupyter Kernel Setup

> 💡 **Beginner Explanation**: Kernels let you use different Python environments within Jupyter. Think of them as "language interpreters" for notebooks.

### Register Environment as Kernel

```bash
mamba activate ds-env
python -m ipykernel install --user --name ds-env --display-name "Data Science (Py3.12)"
```

---

### Verify Installation

```bash
jupyter kernelspec list
```

---

### Kernel Management

```bash
# Remove a kernel
jupyter kernelspec uninstall ds-env
```

> 💡 **Why register kernels?** This allows you to select different Python environments directly in JupyterLab's interface.

---

## 📂 Working Directory Configuration

> 💡 **Beginner Explanation**: This sets where Jupyter looks for your notebooks by default—like setting a "default folder" for your projects.

### Jupyter Notebook

```bash
# Create configuration file if missing
jupyter notebook --generate-config

# Set default directory to ~/projects
echo "c.NotebookApp.notebook_dir = '$HOME/projects'" >> ~/.jupyter/jupyter_notebook_config.py
```

### JupyterLab

```bash
# Create JupyterLab config file
jupyter lab --generate-config

# Set root directory
echo "c.ServerApp.root_dir = '$HOME/projects'" >> ~/.jupyter/jupyter_lab_config.py
```

> 📁 **Important**: Create the directory first: `mkdir ~/projects`

---

## 🖥️ Desktop Integration

### JupyterLab Desktop Shortcut

Create `~/.local/share/applications/jupyterlab.desktop`:

```ini
[Desktop Entry]
Name=JupyterLab
Exec=gnome-terminal -- jupyter-lab --browser="firefox"
Icon=python
Type=Application
Categories=Development;Science;
```

### Launch from Terminal

```bash
# Custom port with no browser auto-open
jupyter-lab --port=8889 --no-browser
```

> 💡 **Beginner Tip**: Desktop shortcuts let you launch JupyterLab like any other application.

---

## 🔧 VS Code Setup

> 💡 **Beginner Explanation**: VS Code is a professional code editor. We'll install it and configure it to work with your Python environment.

### Installing VS Code on Linux

#### DEB (Debian/Ubuntu)
```bash
wget -qO- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > packages.microsoft.gpg
sudo install -D -o root -g root -m 644 packages.microsoft.gpg /etc/apt/keyrings/packages.microsoft.gpg
echo "deb [arch=amd64,arm64,armhf signed-by=/etc/apt/keyrings/packages.microsoft.gpg] https://packages.microsoft.com/repos/code stable main" | sudo tee /etc/apt/sources.list.d/vscode.list
sudo apt update && sudo apt install code
```

#### Snap (All Linux)
```bash
sudo snap install --classic code
```

#### Flatpak (Universal)
```bash
flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
flatpak install flathub com.visualstudio.code
```

---

### Essential Python Extensions

```bash
code --install-extension ms-python.python       # Core Python support
code --install-extension ms-python.vscode-pylance # Smart code completion
code --install-extension ms-toolsai.jupyter     # Notebook support
code --install-extension eamodio.gitlens        # Git history viewer
```

---

### Configuration (`settings.json`)

Open with `Ctrl+Shift+P` → "Preferences: Open User Settings (JSON)":

```json
{
  "python.defaultInterpreterPath": "~/miniforge3/bin/python",
  "python.condaPath": "~/miniforge3/bin/conda",
  "python.analysis.typeCheckingMode": "basic",
  "files.autoSave": "afterDelay",
  "editor.formatOnSave": true
}
```

---

### Miniforge Integration

1. **Select Python Interpreter**:
   - `Ctrl+Shift+P` → "Python: Select Interpreter"
   - Choose `~/miniforge3/bin/python`

> 💡 **Beginner Tip**: This tells VS Code where to find Python and your installed packages.

---

### Recommended Keybindings

| Action | Keybinding | Description |
|--------|------------|-------------|
| Run cell | `Ctrl+Enter` | Executes code cell |
| Show commands | `Ctrl+Shift+P` | VS Code command palette |
| Toggle terminal | `` Ctrl+` `` | Show/hide terminal |

> 🎓 **Learning Tip**: VS Code has excellent interactive tutorials under **Help** → **Interactive Playground**

---

## 🤖 AI Coding Assistants

### JupyterLab Options

```bash
# Codeium (Free AI assistant)
pip install codeium-jupyter

# Jupyter AI (Open-source)
pip install jupyter_ai
```

### VS Code Extensions

1. **Codeium**: Free AI completions
2. **GitHub Copilot**: Popular AI assistant
3. **Gemini**: Google's AI integration

> 🤖 **AI Tips**:
> - Great for learning and code suggestions
> - Always review AI-generated code
> - Free options are good for beginners

---

## 🛠️ Troubleshooting

### Common Issues & Fixes

| Problem | Solution | Why? |
|---------|----------|------|
| **`mamba` not found** | `source ~/miniforge3/etc/profile.d/conda.sh` | Miniforge not loaded |
| **Extensions not loading** | `jupyter lab clean && jupyter lab build` | Needs rebuild |
| **VS Code not finding Python** | Check `python.defaultInterpreterPath` | Wrong path in settings |
| **Package update conflicts** | `mamba update --all` or create new environment | Dependency issues |

---

### Useful Diagnostics

```bash
# Check environment health
mamba doctor

# Show package dependencies
mamba repoquery depends numpy

# List installed packages
mamba list
```

> 🔧 **Help Tip**: Most issues can be solved by:
> 1. Closing and reopening terminals
> 2. Restarting Jupyter/VS Code
> 3. Checking paths in configuration files

---

## 🌐 Resources

- [Miniforge Documentation](https://github.com/conda-forge/miniforge)
- [VS Code Python Tutorial](https://code.visualstudio.com/docs/python/python-tutorial)
- [JupyterLab Interface Guide](https://jupyterlab.readthedocs.io/en/stable/user/interface.html)
- [Conda Cheat Sheet](https://docs.conda.io/projects/conda/en/latest/user-guide/cheatsheet.html)
- [Mamba Package Management](https://mamba.readthedocs.io/en/latest/user_guide/mamba.html)

---

## 🎓 Learning Path

1. **Start** with basic Python in Jupyter
2. **Learn** Pandas for data manipulation
3. **Explore** Matplotlib/Seaborn for visualization
4. **Try** scikit-learn for machine learning

---

*UY1 Néo Quanticiens – Python Tricks Collection*
