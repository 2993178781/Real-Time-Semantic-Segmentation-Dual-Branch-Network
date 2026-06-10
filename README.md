# Real-Time Semantic Segmentation of Complex Road Scenes Based on a Dual-Branch Network

This repository provides the implementation for the manuscript:

**The Real-Time Semantic Segmentation of Complex Road Scenes Based on a Dual-Branch Network**

## Overview

This project focuses on real-time semantic segmentation for complex road scenes in autonomous driving. The proposed method is based on a dual-branch segmentation network that combines high-resolution spatial detail extraction and low-resolution global semantic context modeling. An Adaptive Feature Enhancement Module (AFEM) is introduced into the high-resolution branch to improve channel relationship modeling and multi-scale feature extraction.

To improve robustness under adverse weather conditions, this repository also includes a self-training domain adaptation framework based on a teacher-student model. A Visibility Boost Module (VBM) is used to enhance target-domain images and improve pseudo-label quality under foggy and rainy road-scene conditions.

## Main Components

* Dual-branch semantic segmentation network
* Adaptive Feature Enhancement Module (AFEM)
* Visibility Boost Module (VBM)
* Self-training domain adaptation framework
* Cityscapes semantic segmentation training and evaluation
* Cityscapes to Foggy & Rainy Cityscapes domain adaptation

## Repository Structure

```text
Dual-Branch-Road-Scene-Segmentation/
├── README.md
├── requirements.txt
├── train.py
├── test.py
├── inference.py
├── configs/
│   ├── cityscapes_afem.yaml
│   └── uda_foggy_rainy_cityscapes.yaml
├── models/
│   ├── ddrnet_afem.py
│   ├── afem.py
│   ├── vbm.py
│   └── domain_adaptation.py
├── datasets/
│   └── README.md
├── tools/
│   ├── preprocess_cityscapes.py
│   └── evaluate_miou.py
├── checkpoints/
│   └── README.md
└── docs/
```

## Dataset

The experiments are conducted on the Cityscapes dataset and Foggy & Rainy Cityscapes. Due to dataset license restrictions, the original datasets are not redistributed in this repository. Users should download the datasets from their official sources and organize them according to the instructions in `datasets/README.md`.

## Environment

The experiments were conducted using Python 3.9.18 and PyTorch 2.1.2. The main hardware platform was an NVIDIA GeForce RTX 4090 D GPU.

## Installation

```bash
pip install -r requirements.txt
```

## Training

For standard Cityscapes training:

```bash
python train.py --config configs/cityscapes_afem.yaml
```

For domain adaptation from Cityscapes to Foggy & Rainy Cityscapes:

```bash
python train.py --config configs/uda_foggy_rainy_cityscapes.yaml
```

## Evaluation

```bash
python test.py --config configs/cityscapes_afem.yaml --checkpoint checkpoints/model.pth
```

## Data Availability

The source code and configuration files are provided in this repository. The original Cityscapes and Foggy & Rainy Cityscapes datasets are not redistributed here due to dataset license restrictions. Users should obtain the datasets from their official sources.

## Citation

If you use this code, please cite the related manuscript:

The Real-Time Semantic Segmentation of Complex Road Scenes Based on a Dual-Branch Network.
