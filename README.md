<p align="center">
  <h1 align="center">MORPH-IDS</h1>
  <p align="center">
    <strong>MORPH-IDS: A Drift-Aware Moving Target Defense Framework for Robust Intrusion Detection under Adversarial Drift Environments</strong>
  </p>
  <p align="center">
    <a href="#installation">Installation</a> •
    <a href="#usage">Usage</a> •
    <a href="#project-structure">Structure</a>
  </p>
</p>

---

<p align="center">
  <img src="High-level-design.png" alt="High-Level Design">
  <br>
  <em>High-level architecture of MORPH-IDS. The Defender and Attacker agents co-evolve through continuous interaction, managed by adaptive mechanisms including drift detection and continual learning.</em>
</p>

---

## Installation

```bash
# PyTorch (CUDA 12.1)
pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu121

# Required packages
pip install numpy pandas scikit-learn scipy matplotlib seaborn tqdm joblib

# For Scenario 2 & 3 (adversarial attacks)
pip install adversarial-robustness-toolbox

# For Scenario 1 (CIC-APT-IIoT-2024) & Scenario 4 (class imbalance)
pip install imbalanced-learn
```

**Tested on:** Python 3.11/3.12, CUDA ≥ 12.1, GPU ≥ 16 GB VRAM (NVIDIA P100/T4).

---

## Data Preparation

1. Download dataset from CIC:
   - [CIC-IDS2017](https://www.unb.ca/cic/datasets/ids-2017.html) — Scenarios 1–3
   - [CIC-IDS2019](https://www.unb.ca/cic/datasets/ddos-2019.html) — Scenario 1
   - [CIC-APT-IIoT-2024](https://www.unb.ca/cic/datasets/iiot-dataset-2024.html) — Scenarios 1 & 4
2. Upload dataset to [Kaggle Datasets](https://www.kaggle.com/datasets)
3. Attach dataset to your Kaggle notebook

> Preprocessing (cleaning, normalization, train/val/test split) is handled automatically inside each notebook.

---

## Project Structure

```
├── Scenario1/                              # Baseline Detection
│   ├── CIC-IDS2017/
│   │   ├── morphids-cicids2017.ipynb       # MORPH-IDS
│   │   ├── apollon-cicids2017.ipynb        # Apollon baseline (ML pool)
│   │   └── apollon-cicids2017-DLpool.ipynb # Apollon baseline (DL pool)
│   ├── CIC-IDS2019/
│   │   ├── morphids-cicids2019.ipynb
│   │   ├── apollon-cicids2019.ipynb
│   │   └── apollon-cicids2019-DLpool.ipynb
│   └── CIC-APT-IIOT-2024/
│       ├── morphids-cicapt.ipynb
│       ├── apollon-cicapt.ipynb
│       └── apollon-cicapt-DLpool.ipynb
├── Scenario2/                              # Adversarial Robustness
│   ├── scenario2-morphids.ipynb
│   ├── scenario2-apollon.ipynb
│   └── scenario2-apollon-DL-pool.ipynb
├── Scenario3/                              # Concept Drift Adaptation
│   └── Scenario3-Drift-Adaption.ipynb
└── Scenario4/                              # APT Campaign Detection
    └── Scenario4-APT-Campaigns.ipynb
```

---

## Usage

All notebooks run on [Kaggle](https://www.kaggle.com/) with GPU acceleration.

### Quick Start

1. Create a Kaggle notebook → upload the `.ipynb` file
2. Attach the corresponding dataset
3. **Settings → Accelerator → GPU (P100)** or **TPU**
4. **Run All**

### Scenario 1 — Baseline Detection

Train model pool + RL agent, evaluate detection performance:

```
Scenario1/CIC-IDS2017/morphids-cicids2017.ipynb
Scenario1/CIC-IDS2019/morphids-cicids2019.ipynb
Scenario1/CIC-APT-IIOT-2024/morphids-cicapt.ipynb
```

Compare with Apollon baseline using the corresponding `apollon-*.ipynb` notebooks.

### Scenario 2 — Adversarial Robustness

Evaluate under ZOO and HopSkipJump attacks:

```
Scenario2/scenario2-morphids.ipynb      # MORPH-IDS
Scenario2/scenario2-apollon.ipynb       # Apollon baseline
```

### Scenario 3 — Concept Drift

Test drift adaptation with temporal split and synthetic drift injection:

```
Scenario3/Scenario3-Drift-Adaption.ipynb
```

### Scenario 4 — APT Campaign Detection

Streaming evaluation on CIC-APT-IIoT-2024 with drift detection:

```
Scenario4/Scenario4-APT-Campaigns.ipynb
```

---

<p align="center">
  <sub>Built at the Information Security Lab, University of Information Technology, VNU-HCM</sub>
</p>
