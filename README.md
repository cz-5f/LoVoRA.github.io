# LoVoRA: Text-guided and Mask-free Video Object Removal and Addition with Learnable Object-aware Localization

Zhihan Xiao, Lin Liu†\*, Yixin Gao, Xiaopeng Zhang, Haoxuan Che, Songping Mai\*, Qi Tian   
† Project Leader, \* Corresponding Authors  
📄 **[Project Page](https://cz-5f.github.io/LoVoRA.github.io)**  📚 **[ArXiv](https://arxiv.org/abs/2512.02933)**  💾 **[Dataset](https://huggingface.co/datasets/cz-5f/LoVoRA)(Coming Soon)**  🚧 **Code(Coming Soon)**

---

## 📌 Overview

**LoVoRA** is a novel framework for **text-guided, mask-free video object removal and addition**, designed to achieve high spatial accuracy and strong temporal consistency without requiring auxiliary masks or reference images at inference time.

The core of LoVoRA is a **learnable object-aware localization mechanism**, enabling the model to learn dense spatio-temporal editing regions automatically. Combined with a **Diffusion Mask Predictor**, LoVoRA performs **end-to-end video editing** using only a text prompt and the original video.

---

## 📁 Dataset

The **LoVoRA Dataset** provides high-resolution, instruction-based video editing pairs with strong temporal alignment.

### 🔧 Dataset Generation Pipeline
Our dataset is constructed through the following stages:

1. Image-to-Video (I2V) translation
2. Mask generation from edited images 
3. Optical flow estimation
4. Mask propagation
5. High-quality video inpainting

### 📊 Dataset Comparison

LoVoRA achieves **state-of-the-art VLM evaluation results** based on Prompt Following (PF) and Edit Quality (EQ):

| Dataset        | PF     | EQ     | Generation Basis                              |
|----------------|--------|--------|-----------------------------------------------|
| InsV2V         | --     | --     | Prompt-to-Prompt adaptation                   |
| ICVE-SFT       | --     | --     | Object removal + inpainting                   |
| Senorita-2M    | 3.533  | 3.883  | Object removal + inpainting                   |
| InsViE-1M      | 3.133  | 3.667  | Video inversion + reconstruction              |
| Ditto          | **4.417** | 4.733 | Depth-guided generation                       |
| **Ours**       | 4.375  | **4.850** | **Optical-flow-based mask propagation**       |


---

## 🧠 Method

### 1. Dataset Pipeline
![Dataset Pipeline](static/images/datapipeline.png)

Overview of LoVoRA dataset construction pipeline. Starting from high-quality image editing pairs, we synthesize instruction-based video editing data through five: I2V translation, mask generation, optical flow estimation, mask propagation, and video inpainting.


### 2. Framework Architecture
![Framework](static/images/framework.png)
Overview of the proposed LoVoRA framework. The input video is encoded by a spatio-temporal VAE to produce latents. Encoded latents are channel-concatenated with noisy target latents and processed by a DiT backbone to predict the rectified-flow velocity field. A Diffusion Mask Predictor reads selected DiT token features and predicts a spatio-temporal diff mask used during training.

## 🛠️ Open-Source Plan
- ✅ Project Page  
- ✅ ArXiv  
- ⬜ LoVoRA Dataset
- ⬜ LoVoRA Inference Code
- ⬜ LoVoRA Weights
- ⬜ LoVoRA Dataset Pipeline

## 📑 Citation
```bibtex
@misc{xiao2025lovoratextguidedmaskfreevideo,
  title={LoVoRA: Text-guided and Mask-free Video Object Removal and Addition with Learnable Object-aware Localization},
  author={Zhihan Xiao and Lin Liu and Yixin Gao and Xiaopeng Zhang and Haoxuan Che and Songping Mai and Qi Tian},
  year={2025},
  eprint={2512.02933},
  archivePrefix={arXiv},
  primaryClass={cs.CV},
  url={https://arxiv.org/abs/2512.02933},
}
```



