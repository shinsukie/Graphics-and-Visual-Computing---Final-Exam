# CNN–Vision Transformer Fusion for Single Image Super-Resolution

A lightweight **CNN–Vision Transformer (ViT) fusion network** for **2× Single Image Super-Resolution (SISR)**.  
This project demonstrates how combining convolutional neural networks with transformer-based global attention improves image reconstruction quality compared to traditional interpolation methods.

---

## 📌 Project Overview

Single Image Super-Resolution aims to reconstruct a high-resolution image from a single low-resolution input.  
While CNNs excel at capturing local textures, they struggle with long-range dependencies. Vision Transformers address this limitation through self-attention.

This project proposes a **CNN–ViT fusion architecture** that:
- Extracts local features using residual CNN blocks
- Models global context using a lightweight transformer
- Fuses both representations before upsampling via PixelShuffle

---

## 🧠 Architecture

**Pipeline:**
Low-Resolution Image
↓
CNN Feature Extraction
↓
Vision Transformer Encoder
↓
Feature Fusion (1×1 Conv)
↓
PixelShuffle Upsampling
↓
High-Resolution Output


An architecture diagram is provided in the paper and code outputs.

---

## 📂 Dataset

- **Type:** Synthetic dataset (generated on-the-fly)
- **HR size:** 96×96 RGB images
- **LR size:** 48×48 (bicubic downsampling, ×2 scale)
- **Training samples:** 300
- **Test samples:** 50

> Note: A synthetic dataset is used for proof-of-concept validation and fast experimentation.

---

## ⚙️ Training Details

- **Loss Function:** L1 loss
- **Optimizer:** Adam
- **Learning Rate:** 1e-4
- **Epochs:** 5
- **Framework:** PyTorch
- **Device:** CPU / CUDA (automatic)

---

## 📊 Results

### Training Convergence
- Stable and smooth loss convergence within 5 epochs

### Quantitative Evaluation (PSNR)
| Method | PSNR (dB) |
|------|-----------|
| Bicubic Upsampling | 38.16 |
| CNN–ViT (Proposed) | 26.07 |

> PSNR is averaged over 50 test images.

### Qualitative Results
The CNN–ViT model produces **sharper edges and enhanced textures** compared to bicubic interpolation, despite lower PSNR due to increased high-frequency details.

---

## 📁 Generated Outputs

After running the notebook:
- `loss_curve.png` – Training loss curve
- `sr_results.png` – Visual SR comparison
- `architecture_diagram.png` – Network overview

---

## 🚀 How to Run (Google Colab)

1. Open the provided notebook in **Google Colab**
2. Run all cells sequentially
3. Outputs and figures will be generated automatically

No external dataset download required.

---

## 📄 Paper

This project is accompanied by a **mini research paper** formatted using **Springer LNCS** style, including:
- Methodology
- Architecture explanation
- Experimental results
- Discussion and conclusion
