"""
🧠 CNN vs ViT on Brain MRI Classification
HaloScape Recruitment Case

This project presents a systematic comparison between ResNet-18 (CNN)
and DeiT-Tiny (Vision Transformer) on a multi-class brain MRI tumor
classification task.

Project Scope
-------------
The study evaluates two fundamentally different deep learning paradigms:
- Convolutional Neural Networks (CNNs)
- Vision Transformers (ViTs)

Rather than optimizing solely for leaderboard accuracy, the focus is on:
- Structured data preprocessing
- Transfer learning and fine-tuning strategies
- Stability vs peak performance trade-offs
- Computational efficiency analysis
- Architectural behavior comparison

Dataset
-------
Kaggle Brain Tumor MRI dataset (~3,264 images, 4 classes):
- Glioma
- Meningioma
- Pituitary Tumor
- No Tumor

Data split (stratified):
- Training: 2,296
- Validation: 574
- Test: 394

Preprocessing
-------------
- Resize to 224x224
- RGB conversion
- ImageNet normalization
- Data augmentation (train only):
    * Random horizontal flip
    * ±15° rotation
    * Mild brightness/contrast jitter

Models
------
1) ResNet-18 (CNN baseline)
   - ImageNet pretrained
   - Partial fine-tuning (layer4 + classifier)
   - Dropout (p=0.3)
   - Cosine Annealing scheduler

2) DeiT-Tiny (Vision Transformer)
   - Patch size: 16x16 (196 patches)
   - Full fine-tuning
   - AdamW optimizer
   - Lower learning rate for stability

Test Results
------------
ResNet-18:
- Accuracy: 77.92%
- Macro F1: 0.7528

DeiT-Tiny:
- Accuracy: 74.11%
- Macro F1: 0.6977

Key Findings
------------
- ResNet-18 provides more stable convergence and slightly higher test accuracy.
- DeiT-Tiny achieves competitive performance with significantly fewer parameters
  and faster training/inference.
- Glioma classification remains the most challenging class for both models.
- Vision Transformers show strong efficiency potential for scalable deployment.

Conclusion
----------
CNNs remain a strong baseline for limited medical datasets.
Vision Transformers demonstrate promising efficiency and scalability advantages.
Model stability is as critical as peak accuracy in medical AI applications.
"""
