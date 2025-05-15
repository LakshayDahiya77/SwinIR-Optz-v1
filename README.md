# 🧠 Super-Resolution Using SwinIR with Dynamic Window Attention

This project implements a modified version of the **SwinIR (Swin Transformer for Image Restoration)** architecture to perform 4× single image super-resolution (SISR) using dynamic window attention. The goal was to enhance low-resolution images (128×128) to high-resolution outputs (512×512) by learning spatially adaptive features.

---

## 🚀 Project Overview

- **Architecture**: Custom SwinIR variant with **dynamic window sizing** instead of fixed 8×8 windows.
- **Objective**: Reconstruct high-resolution images with finer texture preservation and better perceptual quality.
- **Datasets**: [DIV2K](https://data.vision.ee.ethz.ch/cvl/DIV2K/) (800 images), [Flickr2K](https://cv.snu.ac.kr/research/Flickr2K/) (2650 images)
- **Upscaling Factor**: 4× (128×128 → 512×512)
- **No pretrained weights used** – trained from scratch due to architectural modifications.

---

## 🏗️ Key Modifications

| Component             | Modified Version                          | Original SwinIR               |
|----------------------|-------------------------------------------|-------------------------------|
| **Windowing**         | `DynamicWindowAttention` module            | Fixed-size Swin attention     |
| **Architecture**      | Lightweight with dynamic Swin blocks      | Hierarchical residual blocks  |
| **Upsampling**        | Direct upsampling after transformer blocks| PixelShuffle reconstruction   |
| **Focus**             | Spatial adaptability                      | Hierarchical deep features    |

---

## 📊 Performance

| Metric       | Value         |
|--------------|---------------|
| **PSNR**     | 28.6 dB       |
| **SSIM**     | 0.89          |
| **Batch Size** | 8 (Colab) / 12 (Kaggle) |
| **Epochs**   | 10 (Colab) + 35 (Kaggle) |
| **GPU Used** | NVIDIA Tesla T4 ×2      |

⚠️ Note: Our model underperformed slightly compared to original SwinIR due to simplified architecture and fewer training optimizations.

---

## 📓 Notebook Link

- 🔗 [Colab Notebook (Training)](https://colab.research.google.com/drive/1gSMlOKq1DgLb6HRgBuG8KNm5fGBVZAHE)
- 🔗 [Colab Notebook (Inference)](https://colab.research.google.com/drive/1JvBTRkgJlB2MCJ9qRNlRRqVMS7a-LZMB)

---

## 💾 Model Weights

- swinsr_epoch_45.pth file in the repo.

---

## 🧠 Lessons Learned

- Always match library versions with pretrained models or architecture dependencies.
- Training large models like SwinIR requires memory-efficient techniques (e.g., mixed precision, gradient accumulation).
- Simple architectural changes (like dynamic window sizing) require extensive tuning to outperform standard methods.

---

## 📌 References

- [Original SwinIR GitHub Repo](https://github.com/JingyunLiang/SwinIR)
- Papers: Liang et al., “SwinIR: Image Restoration Using Swin Transformer”
