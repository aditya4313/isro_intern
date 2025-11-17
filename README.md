# 🛰️ ISRO Internship Project – Attentive-RSIDNet  
### 🚀 A Two-Stage Deep Learning Framework for Remote Sensing Image Denoising

This repository contains the implementation and results of my ISRO internship project, where I developed **Attentive-RSIDNet**, a robust image denoising framework designed specifically for **remote sensing satellite imagery** affected by **structured noise** like banding and striping.

The goal was to create a solution that removes heavy sensor-induced noise while preserving fine image details — something classical filters struggle with.

---

## 🌌 Overview

Satellite images often suffer from **vertical/horizontal stripes, banding, and sensor errors**.  
To solve this, I designed a **hybrid two-stage denoising pipeline**:

### **🔹 Stage 1 — Classical Filtering**
Used to weaken strong striping/banding patterns in the input image.

### **🔹 Stage 2 — Deep Learning Model (Attentive-RSIDNet)**
A CNN enhanced with:

- 🧠 **Multi-Scale Feature Extraction**
- 🎯 **Residual Attention Blocks (ERABs)**
- 👁️ **CBAM Attention (Channel + Spatial)**
- 🔁 **Global Residual Learning**

This combination allows the network to **focus on important features** and **suppress noise intelligently**.

---

## ✨ Key Features

✔ Removes structured noise (banding/striping)  
✔ Attention-driven feature refinement  
✔ Multi-scale texture learning  
✔ Strong generalization across real-world satellite images  
✔ Outperforms classical and modern deep learning baselines  
✔ Pixel-level fidelity with ground truth  

---

## 📂 Dataset Summary

### **Real Satellite Dataset**
- Contains natural striping & banding noise.
- Clean ground truth generated using **sensor-specific LUT correction**.
- Original resolution: *12333 × 12333*
- Converted into **128 × 128 patches** (~13,000 patches)
- 90% training • 10% testing

### **Synthetic Dataset**
To increase robustness and prevent overfitting:
- Airport + Forest images  
- Artificial banding noise added  
- Same patch size: **128 × 128**

---

## 🧠 Model Architecture (Simplified)

### 1️⃣ Multi-Scale Feature Extraction  
Captures fine and coarse patterns using 1×1, 3×3, 5×5, 7×7 convolutions.

### 2️⃣ Enhanced Residual Attention Block (ERAB)  
Includes:
- Two Conv-BN-ReLU layers  
- Residual skip connection  
- **CBAM**:  
  - Channel Attention → *what to focus on*  
  - Spatial Attention → *where to focus on*

### 3️⃣ Noise Residual Learning  
The model predicts **noise**, not the clean image:


This leads to sharper, more accurate reconstructions.

---

## 🧪 Training Details

- Framework: **TensorFlow**
- GPU: **NVIDIA A100 (80 GB)**
- Epochs: **120**
- LR: **1e-3 (cosine annealing)**
- Optimizer: **Adam**
- Loss: **MSE**
- Activation: ReLU  
- Normalization: BatchNorm  

---

# 📊 Results

Below are sample visual comparisons between different denoising methods.  
(*Replace the placeholder links with your actual image paths inside your repo’s `results/` folder.*)

---

## 🖼️ **Result Example 1 — Satellite Image (Structured Noise)**

| Noisy Image | BM3D | Total Variation | DnCNN |
|------------|------|----------------|--------|
| ![noisy](results/noisy1.png) | ![bm3d](results/bm3d1.png) | ![tv](results/tv1.png) | ![dcnn](results/dcnn1.png) |

| RSIDNet (w/o CBAM) | **OURS (Attentive-RSIDNet)** | Ground Truth |
|--------------------|-----------------------------|----------------|
| ![rsid](results/rsid1.png) | ![ours](results/ours1.png) | ![gt](results/gt1.png) |

---

## 🖼️ **Result Example 2 — Aeroplane Dataset (Challenging Case)**

| Noisy Image | BM3D | Total Variation | DnCNN |
|------------|------|----------------|--------|
| ![noisy2](results/noisy2.png) | ![bm3d2](results/bm3d2.png) | ![tv2](results/tv2.png) | ![dcnn2](results/dcnn2.png) |

| RSIDNet (w/o CBAM) | **OURS Model** | Ground Truth |
|--------------------|----------------|----------------|
| ![rsid2](results/rsid2.png) | ![ours2](results/ours2.png) | ![gt2](results/gt2.png) |

---

## 🏆 Quantitative Results

### **Table 1 — Standard Satellite Test Image**

| Method | PSNR (dB) | SSIM |
|--------|-----------|--------|
| BM3D | 14.54 | 0.3832 |
| Total Variation | 17.57 | 0.4279 |
| DnCNN | 24.81 | 0.6621 |
| RSIDNet (No CBAM) | 27.04 | 0.8527 |
| **OURS (Attentive-RSIDNet)** | ⭐ **31.29** | ⭐ **0.9365** |

---

### **Table 2 — Aeroplane Dataset (Hard Case)**

| Method | PSNR (dB) | SSIM |
|--------|-----------|--------|
| BM3D | 13.97 | 0.3342 |
| Total Variation | 17.28 | 0.4049 |
| DnCNN | 25.09 | 0.7602 |
| RSIDNet (No CBAM) | 23.05 | 0.8053 |
| **OURS Model** | ⭐ **27.54** | ⭐ **0.8713** |

---

# 🎯 Pixel-Level Fidelity

The model produces pixel intensities that closely follow a **1:1 correlation** with the ground truth.  
This ensures:
- No color bias  
- No over-smoothing  
- Accurate reconstruction of shadows, highlights, and textures  

---

# 🙌 Acknowledgements

This project was completed as part of my internship at:

**🇮🇳 ISRO — Space Applications Centre (SAC)**  
Under the guidance of:  
**Tushar Shukla (Scientist/Engineer – SD)**

---

# ⭐ If You Found This Helpful  
Please ⭐ **star this repository** and share your feedback!


