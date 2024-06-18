# Latent Diffusion for Geomodel Parameterization

Code example for "Latent diffusion models for parameterization and data assimilation of facies-based geomodels"[ARXIV LINK]

## Summary
Geological parameterization entails the representation of a geomodel using a small set of latent variables and a mapping from these variables to grid-block properties such as porosity and permeability. Parameterization is useful for data assimilation (history matching), as it maintains geological realism while reducing the number of variables to be determined. We present a deep-learning geological parameterization for complex facies-based geomodels, using recently developed generative latent diffusion models (LDMs), first published by [Rombach et al. (2022)](https://arxiv.org/abs/2112.10752). Diffusion models are trained to ''denoise'', which enables them to generate new geological realizations from input fields characterized by random noise. Based on Denoising Probabilstic Diffusion Models (DDPMs), introduced by [Ho et al. (2020)](https://arxiv.org/abs/2006.11239), the LDM representation reduces the number of variables to be determined during history matching, while preserving realistic geological features in posterior models. The model developed in this work includes a variational autoencoder (VAE) for dimension reduction, a U-net for the denoising process, and a Denoising Diffusion Implicit Model (DDIM, [Song et al. (2021)](https://arxiv.org/abs/2010.02502)) noise scheduling for inference.
\
\
Our application involves conditional 2D three-facies (channel-levee-mud) systems. The LDM can provide realizations that are visually consistent with samples from geomodeling software. General agreement between the diffusion-generated models and reference realizations can be observed through quantitative metrics involving spatial and flow-response statistics. The smoothness of the parameterization method can be assessed through latent-space interpolation tests. The LDM can then used for ensemble-based data assimilation. Significant uncertainty reduction, posterior P<sub>10</sub>-P<sub>90</sub> forecasts that generally bracket observed data, and consistent posterior geomodels, can be achieved.

## Contents
- `scripts/` - Directory to store dataset for data preparation, variational autoencoder (VAE) training and U-net training `.py` scripts.
- `data/` - Directory to store training dataset used in this study (2D, three-facies channelized geomodels). Dataset is stored as datasets.Dataset folder (`diffusers_dataset/`) 
- `testing/` - Directory to store reference (geomodeling software-generated) and LDM-generated ensembles used for flow simulations and history matching. Synthetic "true" models used in history matching are saved as `m_true_1.npy` and `m_true_2.npy`. Both are stored as `.npy` files.

Code implementations are based on the following repositories:
- [diffusers](https://github.com/huggingface/diffusers/)
- [monai](https://github.com/Project-MONAI/tutorials/tree/main/generative)

## Software requiremenets
Running the scripts requires the libraries `datasets`,  `diffusers`,  `monai` or  `monai-generative`.
\
This workflow is tested with Python 3.9 and PyTorch 1.8 (CPU/GPU).

## Contact
Guido Di Federico, Louis J. Durlofsky  
Department of Energy Science & Engineering, Stanford University 
\
Contact: gdifede@stanford.edu

