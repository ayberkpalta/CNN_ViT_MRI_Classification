
🧠 CNN vs ViT on Brain MRI Classification

A systematic experimental comparison between ResNet-18 (CNN) and
DeiT-Tiny (Vision Transformer) on a multi-class brain MRI tumor
classification task.


PROJECT OVERVIEW

This project investigates a supervised medical image classification
problem using two fundamentally different deep learning paradigms:

1) Convolutional Neural Networks (CNNs)
2) Vision Transformers (ViTs)

Rather than focusing purely on maximizing leaderboard accuracy,
the study emphasizes:

- Structured data exploration and preprocessing
- Transfer learning and fine-tuning strategies
- Stability vs peak performance trade-offs
- Computational efficiency comparison
- Architectural behavior analysis

Two ImageNet-1k pretrained backbone models are evaluated:

- ResNet-18        → CNN baseline
- DeiT-Tiny (Ti/16) → Efficient Vision Transformer



DATASET
-------
Kaggle Brain Tumor MRI Dataset
- ~3,264 MRI images
- 4 classes:
    • Glioma
    • Meningioma
    • Pituitary Tumor
    • No Tumor

Stratified split:
    - Training:   2,296
    - Validation:   574
    - Test:         394

Stratification ensures class balance across all splits.




PREPROCESSING PIPELINE
----------------------
- Resize to 224 × 224
- RGB conversion
- ImageNet normalization
- Data augmentation (training only):
    • Random horizontal flip
    • ±15° rotation
    • Mild brightness/contrast jitter

Custom PyTorch Dataset and DataLoader implementations
were used for modularity and reproducibility.




MODELS
------

1) ResNet-18 (CNN Baseline)
   - ImageNet pretrained
   - Partial fine-tuning strategy:
        * Early layers frozen
        * layer4 + classifier unfrozen
   - Dropout (p = 0.3)
   - Cosine Annealing learning rate scheduler

2) DeiT-Tiny (Vision Transformer)
   - Patch size: 16 × 16 (196 patches per image)
   - Full fine-tuning
   - AdamW optimizer
   - Lower learning rate for improved stability




TEST PERFORMANCE
----------------
ResNet-18:
    Accuracy  = 77.92%
    Macro F1  = 0.7528

DeiT-Tiny:
    Accuracy  = 74.11%
    Macro F1  = 0.6977




KEY OBSERVATIONS
----------------
- ResNet-18 shows more stable convergence and smoother validation behavior.
- DeiT-Tiny achieves competitive performance with significantly fewer parameters.
- Glioma classification is the most challenging class for both models.
- Vision Transformers demonstrate strong efficiency advantages in
  training speed and inference latency.
- Stability and reliability are critical in medical AI settings,
  not just peak validation metrics.




CONCLUSION
----------
CNNs remain a strong baseline for limited medical imaging datasets.
Vision Transformers offer promising efficiency and scalability benefits,
especially for deployment-sensitive environments.
Model robustness and interpretability are as important as raw accuracy
in high-stakes medical applications.



