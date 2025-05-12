# 🐸 RibbID

**RibbID** is a bioacoustic machine learning project designed to identify multiple species of frogs and toads (order *Anura*) in field audio recordings from Catalonia (northern Spain). Leveraging convolutional neural networks on spectrogram inputs and classical baselines, the model can detect the presence of one or more of **nine target species** within a single recording.

---

## 📑 Table of Contents

1. [Project Overview](#project-overview)
2. [Target Species](#target-species)
3. [Repository Structure](#repository-structure)
4. [Installation](#installation)
5. [Data Organization](#data-organization)
6. [Usage](#usage)
7. [Development & Contributing](#development--contributing)
8. [License](#license)

---

## 🧠 Project Overview

The goal of **RibbID** is to provide researchers and conservationists with a tool to automatically detect and identify multiple frog species from a single audio recording. By focusing exclusively on frogs native to Catalonia, the model is specialized for local biodiversity monitoring and can be integrated into desktop or mobile applications for real‑time or batch inference.

### 🔑 Key Features

- **Multi‑label classification**: Detect more than one species in the same clip.
- **Local species focus**: Optimized for nine common Catalan frog species.
- **Flexible deployment**: Exportable to TensorFlow Lite, ONNX, or PyTorch Mobile.
- **Reproducible pipeline**: Clear directory structure, documented notebooks, and modular source code.

---

## 🐸 Target Species

The model is trained to identify the following species of *Anura* found in Catalonia, northern Spain:

1. **Alytes obstetricans** *(Common midwife toad)*
2. **Bufo spinosus** *(Spiny toad)*
3. **Discoglossus pictus** *(Painted frog)*
4. **Epidalea calamita** *(Natterjack toad)*
5. **Hyla meridionalis** *(Mediterranean tree frog)*
6. **Pelobates cultripes** *(Western spadefoot)*
7. **Pelodytes punctatus** *(Common parsley frog)*
8. **Pelophylax spp.** *(Green frogs complex)*
9. **Rana temporaria** *(Common frog)*

---

## 🗂️ Repository Structure

```plaintext
RibbID/
├── data/
│   ├── raw/             # Original field recordings (.wav/.flac)
│   ├── processed/       # Extracted features (MFCC, spectrogram arrays)
│   └── cleaned/         # Final cleaned metadata and filtered recordings
│
├── notebooks/           # Numbered Jupyter Notebooks for EDA, preprocessing, training
│   ├── 01_exploration.ipynb
│   ├── 02_preprocessing.ipynb
│   └── final.ipynb      # Clean notebook for demo and reporting
│
├── src/                 # Source code modules and scripts
│   ├── preprocessing.py  # Audio loading, normalization, segmentation
│   ├── features.py       # MFCC and spectrogram extraction
│   ├── train.py          # Model definition, training loop
│   └── inference.py      # Inference utilities and multi-label output
│
├── models/              # Saved model checkpoints and exported artifacts
├── reports/             # Generated figures, HTML/PDF notebooks, presentations
├── environment.yml      # Conda environment specification
├── requirements.txt     # Pip requirements (if used)
├── .gitignore           # Ignore patterns for Git
└── README.md            # Project overview and instructions


This project is licensed under the **MIT License**. See [LICENSE](LICENSE) for details.

