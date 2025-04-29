# Comparative Study of Classical and Deep Learning Methods for Multi-Modal Brain Image Registration

## Introduction

Multi-modal medical image registration is a fundamental task in medical imaging, aiming to spatially align anatomical structures across images acquired with different modalities such as CT and MRI. Accurate registration is critical for applications like diagnosis, treatment planning, and neuroanatomical studies.

Classical registration methods typically optimize handcrafted similarity metrics under parametric transformation models. While effective for rigid alignment, they often fail under large intensity variations or non-rigid deformations.

Deep learning-based methods, by contrast, learn transformation priors directly from data, enabling flexible and complex deformation modeling. This project presents a comparative study of classical and deep learning registration algorithms on the RIRE dataset, evaluating anatomical fidelity, accuracy (SSIM, MSE), and computational efficiency. The evaluation focuses on 14 subjects from the RIRE dataset that include both CT and MRI scans. This controlled setup enables a focused and reproducible comparison across classical and deep learning methods without introducing external dataset variability.

------

## Overview

This project conducts a comparative study of classical and deep learning methods for multi-modal brain image registration (CT–MRI) using the RIRE dataset.
Methods are evaluated by registration accuracy (SSIM, MSE), anatomical plausibility, and runtime efficiency.

------

## Repository Structure

| Folder                   | Description                                                  |
| ------------------------ | ------------------------------------------------------------ |
| `classical_methods/`     | Classical 2D registration methods (MI, NCC, FFT, Deformable, RANSAC-SIFT) |
| `deep_learning_methods/` | Deep learning pipelines (BrainMorph, LapIRN, uniGradICON)    |
| `results/`               | Evaluation metrics (CSV) and visualizations                  |

------

## Dataset

The RIRE dataset is not included in this repository. You can download it here:

**Download RIRE Dataset:** [Google Drive Link](https://drive.google.com/file/d/10l0_R8nPLty_kgWmsCGZ22e4Hv6uumEd/view?usp=sharing)

After downloading, structure the dataset as:

```plaintext
rire/
    101/
        ct/patient_101_ct.mhd
        mr_T1/patient_101_mr_T1.mhd
    102/
        ct/
        mr_T1/
    ...
```

Adjust dataset paths inside notebooks and scripts accordingly.

------

## How to Run

| Task              | Command/Notebook                               |
| ----------------- | ---------------------------------------------- |
| Classical Methods | `python classical_methods/bmir_traditional.py` |
| BrainMorph        | Run `deep_learning_methods/brainmorph.ipynb`   |
| LapIRN            | Run `deep_learning_methods/lapirn.ipynb`       |
| uniGradICON       | Run `deep_learning_methods/unigradicon.ipynb`  |

Each script or notebook performs:

- Preprocessing (normalization, resizing)
- Image registration
- Visualization of fixed, moving, and warped images
- Evaluation (SSIM, MSE)
- Saving metrics and results in `results/`

**Note**: Ensure that dataset paths inside the code point to your downloaded `rire/` folder.

------

## Results Summary

| Method            | SSIM (↑) | MSE (↓) | Comments                               |
| ----------------- | -------- | ------- | -------------------------------------- |
| LapIRN            | Best     | Best    | Robust, stable deformations            |
| BrainMorph        | High     | Medium  | Accurate, risk of TPS overshooting     |
| uniGradICON       | Medium   | Medium  | Good global alignment, minor smoothing |
| Classical Methods | Lower    | Higher  | Fast but less reliable for multi-modal |

------

## License

This project is licensed under the MIT License.

------

## Citation

```bibtex
@misc{BMIR2025,
  author = {Waleed Khamies},
  title = {BMIR: Comparative Study of Classical and Deep Learning Methods for Multi-Modal Brain Image Registration},
  year = {2025},
  publisher = {GitHub},
  howpublished = {\url{https://github.com/YourUsername/BMIR}},
}
```