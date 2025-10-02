# ColabReaction: Accelerating Transition State Searches with Machine Learning Potentials on Google Colaboratory 

This repository contains a Google Colab notebook for transition state (TS) search using the Direct MaxFlux (DMF) method and ML potentials (UMA).

# 📘 Colab Notebook

[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://ColabReaction.net)

<a href="https://ColabReaction.net" target="_blank">
  <img src="TOC_logo.jpg" alt="Logo" width="600">
</a>

# 📂 How to Use

1. Click the Colab link above
2. Upload your input files (e.g. `reactant.xyz`, `product.xyz`)
3. Follow the notebook cells

### 📘 User Guide (<a href="https://bilab.github.io/ColabReaction/User_Guide_EN.pdf">English</a>, <a href="https://bilab.github.io/ColabReaction/User_Guide_JP.pdf">日本語</a>)

# 🖥️ Installation for local environment

Although we recommend running this notebook on **Google Colaboratory**, it can also be installed and executed in a local computing environment.
The procedure described below was tested on a standalone local server running **Fedora 40 (conda 25.7.0)** and on a PC cluster managed by the **Torque job scheduler** running **Rocky Linux 8.9 (conda 25.3.1)**.
The installation was performed using **Miniconda3** for environment management.
The following step-by-step instructions provide a reproducible setup for the software environment.


### 1. Create and activate a conda environment
conda create -n colabreaction python=3.11 -y
conda activate colabreaction

### 2. Configure conda channels
conda config --env --remove-key channels 2>/dev/null || true
conda config --env --add channels pytorch
conda config --env --add channels nvidia
conda config --env --add channels conda-forge
conda config --env --add channels defaults
conda config --env --set channel_priority strict

### 3. Install essential packages
conda install -y -c conda-forge python=3.11 nodejs=20 rdkit numba jupyterlab ipykernel
python -m pip install --upgrade pip

### 4. Install PyTorch with CUDA support
python -m pip install --index-url https://download.pytorch.org/whl/cu124 torch==2.6.0 torchvision==0.21.0 torchaudio==2.6.0

### 5. Install additional dependencies
python -m pip install --no-cache-dir "panel @ git+https://github.com/luvwinnie/panel@d80acae43fa3"
python -m pip install --no-cache-dir "panel-3dmol @ git+https://github.com/luvwinnie/panel-3dmol.git@1a4398b66c2a"

conda install -y -c conda-forge numpy scipy ase cyipopt 
python -m pip install --no-cache-dir git+https://github.com/shin1koda/dmf.git

### 6. Install PyTorch Geometric libraries
python -m pip install --no-cache-dir pyg-lib torch-scatter torch-sparse torch-cluster torch-spline-conv -f https://data.pyg.org/whl/torch-2.6.0+cu124.html
python -m pip install --no-cache-dir torch-geometric

### 7. Install visualization and auxiliary packages
python -m pip install --no-cache-dir \
  "param==2.2.1" "jupyter_bokeh==4.0.5" "comm==0.2.3" "plotly==6.3.0" "py3Dmol==2.5.2" \
  "fairchem-core==2.3.0" \
  git+https://github.com/shin1koda/dmf.git

conda install -y -c conda-forge ipywidgets

### 8. Register the kernel
python -m ipykernel install --user --name=colabreaction --display-name "Python (colabreaction)"

### 9. Launching JupyterLab
Before launching JupyterLab, please ensure that the file **Local_ColabReaction.ipynb** is placed in the working directory from which you will start JupyterLab. This ensures that all relative paths and dependencies are correctly resolved.

### 9-1. On a standalone local server
(run on the server):
jupyter lab --no-browser --port=8888 --ip=127.0.0.1 
(run on your local machine, in a web browser):
Open the following URL:
http://localhost:8888

### 9-2. Within a Torque-managed environment
(run on the server, to allocate a compute node):
qsub -I -q <queue_name> -l nodes=<compute_node>:ppn=8:gpus=1,walltime=01:00:00
jupyter lab --no-browser --port=8888 --ip=127.0.0.1
(run on the server, once the compute node is allocated):
ssh -J <username>@<headnode> -L 8890:localhost:8888 <username>@<compute_node>
(run on your local machine, from a separate terminal):
Open the following URL:
http://localhost:8890

Note: For convenience, it is recommended to configure the LocalForward option in your ~/.ssh/config file.


# 📖 Citation

If you use **ColabReaction** in your research, please cite the following publication:

1. Karasawa, M.; Leow, C. S.; Yajima, H.; Arai, S.; Nishizaki, H.; Terada, T.; Sato H. *ChemRxiv* **2025**. DOI: [10.26434/chemrxiv-2025-zvkqk](https://dx.doi.org/10.26434/chemrxiv-2025-zvkqk)

We also recommend citing the following references related to the underlying **DMF/UMA** methodology:

2. Nakano, M.; Karasawa, M.; Ohmura, T.; Terada, T.; Sato, H. *ChemRxiv* **2025**. DOI: [10.26434/chemrxiv-2025-md8k6-v2](https://dx.doi.org/10.26434/chemrxiv-2025-md8k6-v2)
3. Koda, S.; Saito, S. Locating Transition States by Variational Reaction Path Optimization with an Energy-Derivative-Free Objective Function. *J. Chem. Theory Comput.* **2024**, *20* (7), 2798-2811.
4. Koda, S.; Saito, S. Flat-Bottom Elastic Network Model for Generating Improved Plausible Reaction Paths. *J. Chem. Theory Comput* **2024**, *20* (16), 7176-7187.
5. Koda, S.; Saito, S. Correlated Flat-Bottom Elastic Network Model for Improved Bond Rearrangement in Reaction Paths. *J. Chem. Theory Comput.* **2025**, 21 (7), 3513-3522.
6. Wood, B. M.; Dzamba, M.; Fu, X.; Gao, M.; Shuaibi, M.; Barroso-Luque, L.; Abdelmaqsoud, K.; Gharakhanyan, V.; Kitchin, J. R.; Levine, D. S.; et al. UMA: A Family of Universal Models for Atoms. *arXiv preprint* **2025**, https://ai.meta.com/research/publications/uma-a-family-of-universal-models-for-atoms.
7. Levine, D. S.; Shuaibi, M.; Spotte-Smith, E. W. C.; Taylor, M. G.; Hasyim, M. R.; Michel, K.; Batatia, I.; Csányi, G.; Dzamba, M.; Eastman, P.; et al. The Open Molecules 2025 (OMol25) Dataset, Evaluations, and Models. *arXiv preprint* **2025**, arXiv:2505.08762. [physics.chem-ph]
8. fairchem; https://github.com/facebookresearch/fairchem

