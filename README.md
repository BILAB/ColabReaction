# ColabReaction: Accelerated Transition State Searches Using Machine Learning Potentials on Google Colaboratory 

This repository contains a Google Colab notebook for transition state (TS) search using the Direct MaxFlux (DMF) method and ML potentials (UMA).

## 📘 Colab Notebook

[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://ColabReaction.net)

## 📂 How to Use

1. Click the Colab link above
2. Upload your input files (e.g. `reactant.xyz`, `product.xyz`)
3. Follow the notebook cells

## 🖥️ Installation (for local environment)

We recommend running this notebook on Google Colab.

If you wish to use it locally, you may try installing the required packages using:

```bash
pip install -r requirements.txt
```

Some packages may require additional manual installation (e.g., rdkit, dmf, fairchem-core, and custom Panel extensions).
Please refer to the respective project repositories for details.

⚠️ Note: We do not officially support or test local installations.

## Citation

If you use this program in your research, please cite the following ref
erences.

1. Nakano, M.; Karasawa, M.; Ohmura, T.; Terada, T.; Sato, H. ChemRxiv
   2025. DOI: 10.26434/chemrxiv-2025-md8k6-v2
2. Koda, S.; Saito, S. Locating Transition States by Variational Reacti
   on Path Optimization with an Energy-Derivative-Free Objective Functi
   on. J. Chem. Theory Comput. 2024, 20 (7), 2798-2811.
3. Koda, S.; Saito, S. Flat-Bottom Elastic Network Model for Generating
   Improved Plausible Reaction Paths. Journal of Chemical Theory and Co
   mputation 2024, 20 (16), 7176-7187.
4. Koda, S.; Saito, S. Correlated Flat-Bottom Elastic Network Model for
   Improved Bond Rearrangement in Reaction Paths. J. Chem. Theory Compu
   t. 2025, 21 (7), 3513-3522.
5. Wood, B. M.; Dzamba, M.; Fu, X.; Gao, M.; Shuaibi, M.; Barroso-Luque
   , L.; Abdelmaqsoud, K.; Gharakhanyan, V.; Kitchin, J. R.; Levine, D.
   S.; et al. UMA: A Family of Universal Models for Atoms. arXiv prepri
   nt 2025, https://ai.meta.com/research/publications/uma-a-family-of-u
   niversal-models-for-atoms.
6. Levine, D. S.; Shuaibi, M.; Spotte-Smith, E. W. C.; Taylor, M. G.; H
   asyim, M. R.; Michel, K.; Batatia, I.; Csányi, G.; Dzamba, M.; Eastm
   an, P.; et al. The Open Molecules 2025 (OMol25) Dataset, Evaluations
   , and Models. arXiv preprint 2025, arXiv:2505.08762 [physics.chem-ph
   ].
7. fairchem; https://github.com/facebookresearch/fairchem
"""
