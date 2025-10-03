
**Q1: Vision Transformer on CIFAR-10**
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

============================================================

**Q2: Text-Driven Image & Video Segmentation with SAM 2**

This notebook segments objects from images using SAM 2, based on user text prompts.

**How it works:**
- Upload an image and specify a text prompt (e.g. "person, dog").
- The pipeline detects regions matching the prompt and segments them.
- Results are shown as overlays and saved in the outputs directory.

**To run:**
1. Upload your image.
2. Run:
results = text_to_segmentation(
image_path="your_image.png",
text_prompt="person, car",
confidence_threshold=0.25,
output_path=str(OUTPUT_DIR / "result.jpg"))

**Notes:**
- For best results, use specific prompts and clear images.
- If nothing is detected, try lowering the `confidence_threshold` or using a smaller model (`SAM_MODEL_SIZE`).
- Video and batch processing are also supported—see notebook for details.
