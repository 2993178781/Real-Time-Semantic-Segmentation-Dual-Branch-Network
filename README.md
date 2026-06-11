# Real-Time Semantic Segmentation of Complex Road Scenes Based on a Dual-Branch Network

This repository provides the implementation and supplementary materials for the manuscript:

**The Real-Time Semantic Segmentation of Complex Road Scenes Based on a Dual-Branch Network**

## Overview

Semantic segmentation is an important component of autonomous driving perception systems because it enables pixel-level understanding of complex road scenes. However, existing semantic segmentation models often face two major challenges: high-accuracy models usually require high computational cost, and segmentation performance can degrade significantly under adverse weather conditions such as fog, rain, snow, and low-light environments.

To address these problems, this study proposes a real-time semantic segmentation framework based on a dual-branch network. The network combines a high-resolution branch for spatial detail extraction and a low-resolution branch for global semantic context modeling. An Adaptive Feature Enhancement Module (AFEM) is introduced into the high-resolution branch to improve channel relationship modeling and multi-scale feature extraction without substantially increasing computational cost.

In addition, a self-training domain adaptation framework based on a teacher-student model is designed to improve segmentation robustness under adverse weather conditions. A Visibility Boost Module (VBM) is further introduced to enhance target-domain images and improve pseudo-label quality.

## Main Contributions

* A real-time dual-branch semantic segmentation network for complex road scenes.
* An Adaptive Feature Enhancement Module (AFEM) for improving detail extraction and multi-scale feature representation.
* A self-training domain adaptation framework for adapting from standard road scenes to adverse-weather road scenes.
* A Visibility Boost Module (VBM) for improving target-domain image quality and pseudo-label reliability.
* Comparative experiments and ablation studies on Cityscapes and Foggy & Rainy Cityscapes.

## Method

The proposed framework contains the following main components:

1. **Dual-Branch Semantic Segmentation Network**
   The network contains a high-resolution branch and a low-resolution branch. The high-resolution branch preserves spatial details, while the low-resolution branch extracts global semantic context.

2. **Adaptive Feature Enhancement Module (AFEM)**
   AFEM is used to refine fused high-resolution feature maps. It contains a channel relationship enhancement branch and a multi-scale feature extraction branch.

3. **Self-Training Domain Adaptation Framework**
   A teacher-student model is used to generate pseudo-labels for target-domain samples. The student model is trained using both source-domain labels and target-domain pseudo-labels.

4. **Visibility Boost Module (VBM)**
   VBM enhances adverse-weather images before pseudo-label generation. It includes inversion processing, dynamic saturation adjustment, and an atmospheric scattering model.

## Repository Structure

```text
Real-Time-Semantic-Segmentation-Dual-Branch-Network/
├── README.md
├── LICENSE
├── .gitignore
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
    └── figures/
```

## Dataset

The experiments in this study are conducted using the following datasets:

* **Cityscapes**: used as the source-domain dataset for standard urban road-scene semantic segmentation.
* **Foggy & Rainy Cityscapes**: used as the target-domain dataset for evaluating semantic segmentation performance under adverse weather conditions.

Due to dataset license restrictions, the original Cityscapes and Foggy & Rainy Cityscapes images and annotations are not redistributed in this repository. Researchers should download the datasets from their official sources and organize them according to the instructions in `datasets/README.md`.

A recommended dataset structure is shown below:

```text
datasets/
├── cityscapes/
│   ├── leftImg8bit/
│   └── gtFine/
├── foggy_rainy_cityscapes/
│   ├── leftImg8bit/
│   └── gtFine/
└── README.md
```

## Environment

The experiments were conducted under the following environment:

```text
Programming language: Python 3.9.18
Operating system: Windows 10
Deep learning framework: PyTorch 2.1.2 + CUDA 11.8
CUDA version: CUDA 12.4
GPU: NVIDIA GeForce RTX 4090 D
CPU: Intel Core i7-11700F
```

## Installation

Clone this repository:

```bash
git clone https://github.com/2993178781/Real-Time-Semantic-Segmentation-Dual-Branch-Network.git
cd Real-Time-Semantic-Segmentation-Dual-Branch-Network
```

Install the required packages:

```bash
pip install -r requirements.txt
```

## Training

For standard semantic segmentation training on Cityscapes:

```bash
python train.py --config configs/cityscapes_afem.yaml
```

For domain adaptation from Cityscapes to Foggy & Rainy Cityscapes:

```bash
python train.py --config configs/uda_foggy_rainy_cityscapes.yaml
```

## Evaluation

Evaluate the trained model:

```bash
python test.py --config configs/cityscapes_afem.yaml --checkpoint checkpoints/model.pth
```

## Inference

Run inference on a single image or a folder of images:

```bash
python inference.py --input path/to/image_or_folder --checkpoint checkpoints/model.pth --output outputs/
```

## Experimental Results

On the Cityscapes dataset, the proposed method achieves competitive real-time semantic segmentation performance while maintaining high accuracy. The method obtains:

```text
mIoU: 78.41%
FPS: 79.26
GFLOPs: 88.7
Parameters: 21.13M
```

For domain adaptation from Cityscapes to Foggy & Rainy Cityscapes, the proposed method achieves:

```text
mIoU: 72.2%
```

These results demonstrate that the proposed dual-branch network and domain adaptation framework can improve segmentation accuracy and robustness under complex road-scene conditions.

## Data Availability

The source code and configuration files for the proposed dual-branch semantic segmentation network are available in this GitHub repository:

https://github.com/2993178781/Real-Time-Semantic-Segmentation-Dual-Branch-Network

Supplementary files associated with this study have been deposited in Zenodo and are available at:

[https://doi.org/10.5281/zenodo.20630713](https://zenodo.org/uploads/20630713)

The original Cityscapes and Foggy & Rainy Cityscapes datasets are not redistributed in this repository due to dataset license restrictions. Researchers should obtain these datasets from their official sources.

## Citation

If you use this repository or the supplementary files, please cite the related manuscript and Zenodo record:

```text
Li, Z., Wang, G., Li, P., and Lin, Y. The Real-Time Semantic Segmentation of Complex Road Scenes Based on a Dual-Branch Network. Zenodo. https://doi.org/10.5281/zenodo.20630713
```

## License

This repository is released under the MIT License. See the `LICENSE` file for more details.

## Contact

For questions about the code, dataset preparation, or experimental settings, please contact the corresponding author or open an issue in this repository.
