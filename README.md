🧠 CNN vs ViT on Brain MRI Classification

HaloScape Recruitment Case

A systematic comparison of ResNet-18 (CNN) and DeiT-Tiny (Vision Transformer) on a multi-class brain MRI tumor classification task.

📌 Project Overview

This project addresses a supervised image classification problem on brain MRI scans using two fundamentally different deep learning paradigms:

Convolutional Neural Networks (CNNs)

Vision Transformers (ViTs)

Instead of focusing purely on maximizing leaderboard accuracy, this study emphasizes:

Structured data exploration and preprocessing

Transfer learning & fine-tuning strategies

Stability vs peak performance trade-offs

Computational efficiency comparison

Architectural behavior analysis

Two ImageNet-1k pretrained backbones were compared:

ResNet-18 — CNN baseline

DeiT-Tiny (DeiT-Ti/16) — Efficient Vision Transformer

📊 Dataset

Kaggle Brain Tumor Classification (MRI)

~3,264 MRI images

4 classes:

Glioma

Meningioma

Pituitary tumor

No tumor

Final split:

Split	Images
Training	2,296
Validation	574
Test	394

Stratified splitting was applied to preserve class distribution.

⚙️ Preprocessing Pipeline

Resize to 224 × 224

RGB conversion

ImageNet normalization

Data augmentation (training only):

Random horizontal flip

±15° rotation

Mild brightness/contrast jitter

Custom PyTorch Dataset and DataLoader implementations were used.

🧩 Models
🔹 ResNet-18 (CNN Baseline)

ImageNet-1k pretrained

Partial fine-tuning:

Frozen early layers

Unfrozen layer4 + classification head

Dropout (p=0.3)

Cosine Annealing scheduler

🔹 DeiT-Tiny (Vision Transformer)

Patch size: 16 × 16

196 patches per image

Full fine-tuning

AdamW optimizer

Lower learning rate for stability

📈 Results
🔬 Test Performance
Model	Test Accuracy	Macro F1
ResNet-18	77.92%	0.7528
DeiT-Tiny	74.11%	0.6977
📊 Validation Behavior

ResNet-18

More stable

Faster convergence

Better generalization consistency

DeiT-Tiny

Higher peak validation F1 (0.755)

More volatile across epochs

Sensitive to optimization hyperparameters

🧠 Class-wise Observations

ResNet-18 achieves 100% recall on No Tumor.

Glioma is the most challenging class for both models.

CNN struggles with subtle global tumor differences.

ViT distributes errors differently but still struggles with Glioma.

⚡ Efficiency Comparison
Metric	ResNet-18	DeiT-Tiny
Total Parameters	11.18M	5.53M
Trainable Params	8.40M	0.89M
FLOPs	1.82G	1.07G
Epoch Time	53.16s	17.81s
Inference Time	0.512s	0.191s
🔎 Interpretation

ResNet-18 → More stable & slightly more accurate

DeiT-Tiny → Smaller, faster, more scalable

ViT offers significant efficiency advantages with competitive performance.


