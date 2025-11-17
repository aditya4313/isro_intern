# 🛰️ ISRO Internship Project – Attentive-RSIDNet  
### 🚀 A Two-Stage Deep Learning Framework for Remote Sensing Image Denoising

This repository contains the implementation and results of my ISRO internship project, where I developed **Attentive-RSIDNet**, a robust image denoising framework designed specifically for **remote sensing satellite imagery** affected by structured noise like banding and striping.

The goal was to create a solution that removes heavy sensor-induced noise while preserving fine image details — something classical filters struggle with.

---

## 🌌 Overview

Satellite images often suffer from **vertical/horizontal stripes, banding, and sensor errors**.  
To solve this, I designed a **hybrid two-stage denoising pipeline**:

### 🔹 Stage 1 — Classical Filtering  
Used to weaken strong striping/banding patterns in the input image.

### 🔹 Stage 2 — Deep Learning Model (Attentive-RSIDNet)  
A CNN enhanced with:

- 🧠 Multi-Scale Feature Extraction  
- 🎯 Residual Attention Blocks (ERABs)  
- 👁️ CBAM Attention (Channel + Spatial)  
- 🔁 Global Residual Learning  

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
- Contains natural striping & banding artifacts  
- Clean ground truth created using **sensor-specific LUT correction**  
- Original resolution: **12333 × 12333 pixels**  
- Converted into **128 × 128 patches** (~13,000 total)  
- 90% train • 10% test  

### **Synthetic Dataset**
- Airport + Forest images  
- Artificial banding noise added  
- Same 128 × 128 patch size  
- Helps avoid overfitting and improves generalization  

---

# 🏗️ Model Architecture

Below is the complete architecture diagram of the **Attentive-RSIDNet** framework, including the MSFE block, ERAB block, CBAM attention, and the final residual learning pathway.

*(Replace the link below with your actual architecture image URL once uploaded)*

![architecture](https://github.com/user-attachments/assets/91ea8ebc-fd46-4e1f-8bb8-cbb3ae0f9e8d)


---

## 🧠 Model Architecture (Simplified Text Summary)

### 1️⃣ Multi-Scale Feature Extraction  
4 parallel convolutions: **1×1, 3×3, 5×5, 7×7**  
Captures fine + coarse features simultaneously.

### 2️⃣ Enhanced Residual Attention Block (ERAB)  
- Two Conv + BN + ReLU layers  
- Residual skip connection  
- **CBAM** consisting of:  
  - Channel Attention → focuses on important feature channels  
  - Spatial Attention → highlights important spatial regions  

### 3️⃣ Noise Residual Learning  
Instead of predicting the clean image, the model predicts **noise**:


This strategy gives sharper and more accurate reconstructions.

---

## 🧪 Training Configuration

- Framework: TensorFlow  
- GPU: NVIDIA A100 (80 GB)  
- Epochs: 120  
- Loss Function: MSE  
- Optimizer: Adam  
- Learning Rate: 1e-3 (cosine annealing)  

---

# 📊 Results

Each result image already contains a **complete grid comparison**:  
Noisy • BM3D • TV • DnCNN • RSIDNet(no CBAM) • OURS • Ground Truth  

---

## 🖼️ Result Example 1 — Satellite Image

![result1](https://github.com/user-attachments/assets/545e2167-06d5-45a2-94b6-b28d3a78dd93)

---

## 🖼️ Result Example 2 — Aeroplane Dataset

![result2](https://github.com/user-attachments/assets/54a37bfe-8cfe-4ab5-9c8e-3c8577352d58)

---

# 🏆 Quantitative Evaluation

### **Table 1 — Standard Satellite Test Image**
| Method | PSNR (dB) | SSIM |
|--------|-----------|--------|
| BM3D | 14.54 | 0.3832 |
| Total Variation | 17.57 | 0.4279 |
| DnCNN | 24.81 | 0.6621 |
| RSIDNet (No CBAM) | 27.04 | 0.8527 |
| **OURS (Attentive-RSIDNet)** | ⭐ **31.29** | ⭐ **0.9365** |

---

### **Table 2 — Aeroplane Dataset**
| Method | PSNR (dB) | SSIM |
|--------|-----------|--------|
| BM3D | 13.97 | 0.3342 |
| Total Variation | 17.28 | 0.4049 |
| DnCNN | 25.09 | 0.7602 |
| RSIDNet (No CBAM) | 23.05 | 0.8053 |
| **OURS Model** | ⭐ **27.54** | ⭐ **0.8713** |

---

# 🎯 Pixel-Level Fidelity

The model shows a strong **1:1 correlation** between predicted and ground-truth pixel intensities, ensuring:

- Minimal color or brightness drift  
- High structural consistency  
- Accurate restoration of textures  
- Reliable performance across datasets  

---

# 🙌 Acknowledgements

This research work was completed during my internship at:

**🇮🇳 ISRO — Space Applications Centre (SAC)**  
Mentor: **Tushar Shukla (Scientist/Engineer – SD)**  

---

# ⭐ If You Found This Useful  
Please ⭐ **star the repository** and share your thoughts!

