## Files in this repo
- Q1.ipynb: Vision Transformer for CIFAR-10
- Q2.ipynb: Text-driven segmentation with SAM 2
- README.md: Documentation (this file)

---

## Q1: Vision Transformer on CIFAR-10

**Model Configuration:**  
- ViT-Small/16 (patch=16, image=224, 21.67M params, ImageNet1k pretrain)
- Optimizer: AdamW, lr=1e-4, wd=0.1, batch=64, scheduler: CosineAnnealing (50 epochs)
- Regularization: dropout (0.1), drop path (0.1), label smoothing (0.1)
- Augmentation: resize, crop, horizontal flip, normalization

**Results:**  
- Final test accuracy: **98.1%**
- Pre-trained weights essential – 95%+ in first epoch
- Strong regularization prevented overfitting

---

## Q2: Text-Driven Segmentation with SAM 2

**Summary:**  
Segments objects from images using text prompts with SAM 2.  
Upload an image, enter prompt (e.g. `"person, dog"`), view overlay masks and save results.

**How to run:**  
1. Upload your image in Colab.
2. Run:
results = text_to_segmentation(
image_path="your_image.png",
text_prompt="person, car",
confidence_threshold=0.25,
output_path=str(OUTPUT_DIR / "result.jpg"))

text

**Notes:**  
- Specific prompts with clear images work best.  
- If nothing detected, lower `confidence_threshold` or use smaller `SAM_MODEL_SIZE`.  
- Batch and video segmentation supported (see notebook).  
- All outputs saved to `outputs/` folder.

**Limitations:**  
- RAM/VRAM may limit very large images/videos.  
- Segmentation depends on prompt detail and object visibility.
