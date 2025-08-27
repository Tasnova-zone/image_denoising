# 🖼️ Image Denoising with CNN Autoencoder, UNet, and Pix2Pix GAN

## 📌 Project Overview
This project explores **image denoising** using deep learning.  
We compare three architectures on the **[Natural Images with Synthetic Noise](/kaggle/input/natural-images-with-synthetic-noise)** dataset:  

- **Autoencoder (AE)** → Baseline CNN encoder–decoder  
- **UNet** → Encoder-decoder with skip connections  
- **Pix2Pix GAN (cGAN)** → Adversarial learning for sharper outputs  

Our goal was to evaluate which approach works best for denoising in terms of both **quantitative metrics** and **visual perceptual quality**.

---

## 🎯 Objectives
- Train and evaluate CNN-based models for image denoising.  
- Compare **pixel-wise fidelity metrics** (PSNR, SSIM, MAE).  
- Compare **perceptual sharpness** across AE, UNet, and Pix2Pix.  
- Provide a reproducible end-to-end pipeline.  

---

## 📂 Dataset
- Source: Kaggle – [Natural Images with Synthetic Noise](https://www.kaggle.com/datasets/joaopauloschuler/natural-images-with-synthetic-noise)  
- Structure:  


- Images are RGB, resized to **128 × 128**.

---

## 🏗️ Methodology

### Preprocessing
- Normalize images to `[0,1]`  
- Create paired `(noisy, clean)` datasets  
- Use `tf.data` pipelines with batching + prefetch  

### Models
1. **Autoencoder** – CNN encoder–decoder trained with MSE loss.  
2. **UNet** – Skip connections preserve spatial detail.  
3. **Pix2Pix GAN** – Generator (UNet) + PatchGAN discriminator, trained with:  
 - Adversarial Loss  
 - L1 Loss  
 - SSIM Loss (perceptual consistency)  

### Metrics
- **PSNR** (higher = better)  
- **SSIM** (higher = better)  
- **MAE** (lower = better)  

---

## 📊 Results

| Model        | PSNR (dB) | SSIM   | MAE    |
|--------------|-----------|--------|--------|
| Autoencoder  | **11.49** | **0.270** | **0.2364** |
| UNet         | 11.42     | 0.269  | 0.2367 |
| Pix2Pix v2   | 11.42     | 0.269  | 0.2367 |

- **Autoencoder** performs best on metrics.  
- **UNet** is close, benefiting from skip connections.  
- **Pix2Pix GAN** produces **sharper perceptual images**, though not better in PSNR/SSIM.  

---

## 🖼️ Sample Outputs
_Noisy → Autoencoder → UNet → Pix2Pix → Ground Truth_

*(Insert example image grid here)*  

---

## 🚀 How to Run

### 1. Clone Repo
```bash
git clone https://github.com/yourusername/image-denoising-ml.git
cd image-denoising-ml



