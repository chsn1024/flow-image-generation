# Flow-based Image Generation

> A modified implementation of a normalizing flow model for image generation, based on an open-source Glow / RealNVP framework.

## 1. 项目简介（Introduction）

本项目基于开源 **Normalizing Flow（可逆生成模型）** 图像生成框架进行二次开发，主要目标是：

* 理解 Flow 模型的基本原理与训练流程
* 在原有实现基础上，对模型结构 / 训练过程 / 采样方式进行修改与实验
* 构建一个结构清晰、可复现实验的图像生成项目

该项目用于课程学习与个人研究实践，不以商业用途为目的。

---

## 2. 背景知识（Background）

Normalizing Flow 是一类 **显式建模概率分布** 的生成模型，通过一系列 **可逆变换（invertible transformations）**，将简单分布（如高斯分布）映射到复杂数据分布。

与 GAN / Diffusion 模型相比，Flow 模型具有以下特点：

* 可计算精确对数似然（Exact Log-likelihood）
* 训练过程稳定，不依赖对抗训练
* 推断与生成过程可逆

典型代表模型包括：NICE、RealNVP、Glow 等。

---

## 3. 项目来源与修改说明（Based on & Modifications）

### 3.1 原始项目

本项目基于以下开源项目进行修改：

* Original repository: **https://github.com/rosinality/glow-pytorch**
* Related paper: *Glow: Generative Flow with Invertible 1×1 Convolutions*

感谢原作者提供的开源实现。

### 3.2 本项目的主要修改

在原项目基础上，本项目进行了以下调整：

* 种子固定，可断续训练
---

## 4. 项目结构（Project Structure）

```
flow-image-generation/
├── src/                # 核心源码
├── model.py            # Flow / Glow 模型定义，重点
├── train.py            # 整体项目环境
├── configs/            # 配置文件
├── README.md
└── .gitignore
```

---

## 5. 环境配置（Environment）

* Python 3.x
* PyTorch >= 1.x
* CUDA（可选，用于 GPU 训练）

<!-- 安装依赖：

```bash
pip install -r requirements.txt
``` -->

---

## 6. 使用方法（Usage）

### 6.1 模型训练

先把train.py中图片路径改为你要训练图片的路径：

```bash
python src/train.py
```

可在 `configs/` 中调整训练参数，如 batch size、学习率、网络深度等。

### 6.2 图像生成 / 采样

```bash
python src/sample.py
```

生成的图像将保存在指定输出目录中（默认不纳入 Git 版本控制）。

---

欢迎交流与讨论。
