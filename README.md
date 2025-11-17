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

## 🧪 Training Configuration

- Framework: TensorFlow  
- GPU: NVIDIA A100 (80 GB)  
- Epochs: 120  
- Loss: MSE  
- Optimizer: Adam  
- Learning Rate: 1e-3 (cosine annealing)  

---

# 📊 Results

Below are the final test results.  
Each image already contains a **grid comparison** of:  
Noisy • BM3D • Total Variation • DnCNN • RSIDNet(no CBAM) • OURS • Ground Truth

---

## 🖼️ **Result Example 1 — Satellite Image**
*(Full 4×3 image grid inside this single image)*


![result1](<img width="999" height="613" alt="Screenshot 2025-11-18 at 12 17 01 AM" src="https://github.com/user-attachments/assets/545e2167-06d5-45a2-94b6-b28d3a78dd93" />)

---

## 🖼️ **Result Example 2 — Aeroplane Dataset**
*(Full horizontal grid image inside this single image)*

![result2](<img width="904" height="555" alt="Screenshot 2025-11-18 at 12 16 44 AM" src="https://github.com/user-attachments/assets/54a37bfe-8cfe-4ab5-9c8e-3c8577352d58" />
sult2.png)

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

The model shows strong **1:1 pixel intensity correlation** with the ground truth, ensuring:

- minimal color drift  
- high structural consistency  
- accurate detail recovery  
- robust performance across datasets  

---

# 🙌 Acknowledgements

This research project was completed during my internship at:

**🇮🇳 ISRO — Space Applications Centre (SAC)**  
Mentor: **Tushar Shukla (Scientist/Engineer – SD)**  

---

# ⭐ If You Found This Useful  
Please ⭐ **star the repository** and share your thoughts!

