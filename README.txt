## anuraID

**anuraID** is a bioacoustic machine learning project designed to identify multiple species of frogs and toads (order Anura) in field audio recordings from Catalonia (northern Spain). Leveraging convolutional neural networks on spectrogram inputs and classical baselines, the model can detect the presence of one or more of nine target species within a single recording.

---

## Table of Contents

1. [Project Overview](#project-overview)
2. [Target Species](#target-species)
3. [Repository Structure](#repository-structure)
4. [Installation](#installation)
5. [Data Organization](#data-organization)
6. [Usage](#usage)
7. [Development & Contributing](#development--contributing)
8. [License](#license)

---

## Project Overview

The goal of **anuraID** is to provide researchers and conservationists a tool to automatically detect and identify multiple frog species from a single audio recording. By focusing exclusively on frogs native to Catalonia, the model is specialized for local biodiversity monitoring and can be integrated into desktop or mobile applications for real‑time or batch inference.

**Key Features**:

- **Multi‑label classification:** detect more than one species in the same clip.
- **Local species focus:** optimized for nine common Catalan frog species.
- **Flexible deployment:** exportable to TensorFlow Lite, ONNX, or PyTorch Mobile.
- **Reproducible pipeline:** clear directory structure, documented notebooks, and source modules.

---

## Target Species

The model is trained to identify the following species of Anura found in Catalonia, northern Spain:

1. **Alytes obstetricans** (Common midwife toad)
2. **Bufo spinosus** (Spiny toad)
3. **Discoglossus pictus** (Painted frog)
4. **Epidalea calamita** (Natterjack toad)
5. **Hyla meridionalis** (Mediterranean tree frog)
6. **Pelobates cultripes** (Western spadefoot)
7. **Pelodytes punctatus** (Common parsley frog)
8. **Pelophylax spp.** (Green frogs complex)
9. **Rana temporaria** (Common frog)

---

## Repository Structure

```plaintext
anuraID/
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
│
├── reports/             # Generated figures, HTML/PDF notebooks, presentations
│
├── environment.yml      # Conda environment specification
├── requirements.txt     # Pip requirements (if used)
├── .gitignore           # Ignore patterns for Git
└── README.md            # Project overview and instructions
```

---

## Installation

1. **Clone the repository** (via GitHub website or `git clone`):
   ```bash
   git clone https://github.com/<your_username>/anuraID.git
   cd anuraID
   ```

2. **Set up the Conda environment** (recommended):
   ```bash
   conda env create -f environment.yml
   conda activate anuraID
   ```

3. **(Optional) Install via pip** if you prefer:
   ```bash
   pip install -r requirements.txt
   ```

---

## Data Organization

- Place your raw audio files in `data/raw/` and ensure you have a `metadata.csv` with columns:
  - `filename`, `species`, `date`, `time`, `location`, `notes`

- Processed features (e.g., mel-spectrogram `.npy` files) should go to `data/processed/`.

- Any intermediate cleaned datasets or filtered subsets belong in `data/cleaned/`.

---

## Usage

### Exploratory Analysis

Launch Jupyter Notebook and run the exploration notebook:
```bash
jupyter notebook notebooks/01_exploration.ipynb
```

### Training the Model

Execute the training script:
```bash
python src/train.py \
  --data-dir data/processed \
  --output-dir models/ \
  --epochs 50 \
  --batch-size 32
```

### Inference

Use the inference module to predict species in a new audio file:
```python
from src.inference import predict_multilabel

preds = predict_multilabel("path/to/recording.wav")
print(preds)  # e.g. {"Bufo spinosus": 0.87, "Rana temporaria": 0.45}
```

---

## Development & Contributing

Contributions are welcome! To propose changes:

1. Fork the repository.
2. Create a feature branch (`git checkout -b feature/abc`).
3. Commit your changes and push to your fork.
4. Open a Pull Request explaining your changes.

Please follow the [code style guide](https://github.com/your_username/anuraID/blob/main/src/) and add tests for new functionality.

---

## License

This project is licensed under the **MIT License**. See [LICENSE](LICENSE) for details.

