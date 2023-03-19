
# INSTALLING PYTHON via MINIFORGE or MAMBAFORGE ON LINUX


[![Miniforge](https://github.com/conda-forge/miniforge/actions/workflows/ci.yml/badge.svg)](https://github.com/conda-forge/miniforge/actions/workflows/ci.yml)
[![GitHub downloads](https://img.shields.io/github/downloads/conda-forge/miniforge/total.svg)](https://tooomm.github.io/github-release-stats/?username=conda-forge&repository=miniforge)

**Note**:
* Miniforge is like miniconda, but with the conda-forge channel preconfigured and all packages coming from the conda-forge and not the defaults channel.

* Mambaforge is like miniforge, but has mamba installed into the base environment.

* conda download packages in series while mamba download in parallel. In addition, a package already downloaded with mamba, in an environment, can be installed in another environment without a new download.

Our preference goes to mambaforge or miniforge with mamba option installed.

1. Install Miniforge3 or Mambaforge
     1. Download the file (~64 MB)
    > wget -c https://github.com/conda-forge/miniforge/releases/latest/download/Miniforge3-Linux-x86_64.sh

    > wget -c https://github.com/conda-forge/miniforge/releases/latest/download/Mambaforge-Linux-x86_64.sh

     2. Install (inside the directory where your previously download file is, right click and choose "open in terminal")
    > bash Miniforge3-Linux-x86_64.sh
    
    or
    
    > bash Mambaforge-Linux-x86_64.sh

    Validate the licence and choose "yes" anytime. At the end close the terminal and open it again.
    You should see ">(base)"

    1. Update conda
    >(base) conda update conda -y
    
    or
    
    >(base) mamba update conda -y

    2. Install mamba in miniforge (which is more powerfull and efficient than conda)
    >(base) conda install mamba -y
    
    >(base) mamba init

2. Install some main packages on the "(base)"
>(base) mamba install jupyterlab ipykernel nb_conda_kernels

1. For easy autocompletion with "tabnine" an AI code completion tool
>(base) pip install --upgrade jupyterlab_tabnine

This would install jupyterlab and jupyter notebook. My advice is to use jupyterlab which is modern and powerfull.
"ipykernel" is necessary to the use of one jupyter (lab or notebook) with various kernels or environments


## Installing jupyterlab-katex

>(base) pip install jupyterlab-katex

**jupyterlab-katex** is a JupyterLab extension for rendering KaTeX math.

The default LaTeX renderer in JupyterLab uses MathJax, which, while powerful, can be slow to render complex equations. This extension substitutes the MathJax renderer with the KaTeX renderer. KaTeX is much faster, at the cost of being less full-featured than MathJax. If you want faster math processing and the subset of LaTeX provided by KaTeX is sufficient for your purposes, this may be the extension for you!

If you equations are not rendering properly with this extension, you probably will want to fall back to MathJax.

## CREATE CONDA ENVIRONMENTS

1. To create an environment
>(base) mamba (or conda) create --name myenv -y

For example, to create an qiskit environment
>(base) mamba (or conda) create --name qiskit-env -y

To create an environment with a specific version of Python:

>(base) mamba (or conda) create -n myenv python=3.9

2. To verify that the environment was created
>(base) mamba (or conda) info --envs

or

>(base) mamba (or conda) env list

A list similar to the following is displayed

    >(base) conda environments:
    myenv                 /home/username/miniconda/envs/myenv
    snowflakes            /home/username/miniconda/envs/snowflakes
    bunnies               /home/username/miniconda/envs/bunnies

3. To activate an environment
>(base) mamba (or conda) activate myenv

 which gives

>(myenv)

4. To activate an environment
>(base) mamba (or conda) activate myenv

 which gives

>(myenv)

5. To deactivate an environment
>(myenv) mamba (or conda) deactivate

 which gives

>(base)


## ADDING PYTHON MULTIKERNELS TO CONDA ENVIRONMENTS TO BE OPEN WITH JUPYTER

1. Install the required packages (if there not installed during the steps I.)
>(base) mamba (or conda) install ipykernel nb_conda_kernels -y

2. In each conda environments, including "base", execute
> ipython kernel install --user --name "myenv"

or

> python -m install ipykernel --user --name "myenv"

For example
>(base) ipython kernel install --user

or

>(base) python -m ipykernel install --user

>(base) conda activate qiskit-env

>(qiskit-env) ipython kernel install --user --name "qiskit-env"

or
>(qiskit-env) mamba install ipykernel -y &&  python -m ipykernel install --user --name "qiskit-env"

3. To list kernels
>(base) jupyter kernelspec list

and the output looks as

Available kernels:

  jarvis-env    /home/taamangtchu/.local/share/jupyter/kernels/jarvis-env
  python3       /home/taamangtchu/.local/share/jupyter/kernels/python3
  qiskit-env    /home/taamangtchu/.local/share/jupyter/kernels/qiskit-env


## CHANGING WORKING DIRECTORY UNDER LINUX

1. First you need to create the config file
>(base) jupyter notebook --generate-config

2. View the config file at: ~/.jupyter/jupyter_notebook_config.py

3. Then, Ctrl+F: # c.NotebookApp.notebook_dir ='' .

    Change the line:<br>
    c.NotebookApp.notebook_dir = ''<br>
    to<br>
    c.NotebookApp.notebook_dir = '/path/to/desired/startup/directory'

For example <br>
    c.NotebookApp.notebook_dir = '/media/taamangtchu/MYDATA/Workplace/'

Make sure to remove #, as it is as comment.
Ctrl+S to save the config.py file !!!

{
For those using jupyterlab as me:
>(base) jupyter lab --generate-config

~/.jupyter/jupyter_lab_config.py

c.ServerApp.root_dir = ''
}


## CREATING A JUPYTER DESKTOP SHORTCUT

1. Right clic on the desktop and choose create a new file. Then give the name
"Jupyterlab.desktop"

2. Copy the following, paste inside the file and save

  [Desktop Entry]<br>
  Encoding=UTF-8 <br>
  Name=JupyterLab <br>
  GenericName=JupyterLab <br>
  Comment=Start Jupyter Lab server<br>
  Exec=gnome-terminal --tab -- /bin/bash -c "~/miniconda3/bin/jupyter-lab;bash"<br>
  Icon= jupyter-lab<br>
  Type=Application<br>
  Categories=Development;<br>
  StartupNotify=true<br>
  StartupWMClass=jupyter-lab<br>
  Actions=open-browser<br>

[Desktop Action open-browser]<br>
Name=Open in browser<br>
Exec=xdg-open http://localhost:8888/lab<br>


3. For jupyter notebook, the contain is

[Desktop Entry]<br>
Encoding=UTF-8<br>
Name=Jupyter Notebook<br>
GenericName=Jupyter Notebook<br>
Comment=Start Jupyter Notebook server<br>
Exec=gnome-terminal --tab -- /bin/bash -c "~/miniconda3/bin/jupyter-notebook;bash"<br>
Icon= jupyter-notebook<br>
Type=Application<br>
Categories=Development;<br>
StartupNotify=true<br>
StartupWMClass=jupyter-notebook<br>
Actions=open-browser<br>

[Desktop Action open-browser]<br>
Name=Open in browser<br>
Exec=xdg-open http://localhost:8888/tree<br>

4. Jupyter notebook desktop can directly be install through the software manager
     1. Open the software manager
     2. Type "jupyter notebook" on "search" space
     3. Clic on "Install" when the icon "run jupyter notebook" will appear

