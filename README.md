
**q1: Vision Transformer on CIFAR-10**
============================================================
MODEL CONFIGURATION SUMMARY
============================================================

**Model Architecture:**
- Base Model: ViT-Small/16 (patch_size=16, image_size=224)
- Parameters: 21.67M
- Pre-trained: Yes (ImageNet-1k)

**Training Configuration:**
- Optimizer: AdamW
- Learning Rate: 1e-4
- Weight Decay: 0.1
- Scheduler: CosineAnnealingLR (50 epochs)
- Batch Size: 64
- Label Smoothing: 0.1
- Dropout: 0.1
- Drop Path Rate: 0.1

**Data Augmentation:**
- Resize to 224x224
- Random Crop with padding
- Random Horizontal Flip
- Normalization (ImageNet statistics)
...
3. **Strong regularization** (dropout + drop_path + weight_decay + label smoothing) prevented overfitting
4. **Longer training** (50 epochs) allowed gradual convergence to 98%+
5. **Pre-trained weights** essential - achieved 95%+ in first epoch
