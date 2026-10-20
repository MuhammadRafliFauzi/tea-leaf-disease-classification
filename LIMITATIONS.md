# Reproducibility, ethics, and limitations

- **Original recorded results vs. reproduction:** Original notebooks contain saved output reporting approximately 95% internal accuracy per configuration, external-original accuracies of 71/76/74%, and external AI-edited accuracies of 77/74/80% (LBP/GLCM/HSV). These are results reported in the original thesis experiments; the publicly shared notebook copies do not guarantee independent reproduction.
- **Limited external coverage:** 66 images of four classes, not all six classes. The external dataset is imbalanced and small.
- **Generative editing:** CapCut prompt-based AI image editing was used for the edited external set. The precise model and edit parameters are unknown. The image-editing system may introduce or alter disease-specific visual details, so results should not be interpreted as proof of improved fidelity or generalized robustness.
- **No causal attribution:** Differences between 76% for original images (GLCM) and 80% for edited images (HSV) also change the feature extractor; they cannot be attributed purely to the editing process.
- **Portability:** Paths are placeholders; original research code contains assumptions about Google Colab, Google Drive, dataset folders, and local caches. The published notebook copies are provided primarily for code review, not guaranteed push-button execution.
- **No dataset/model redistribution:** Raw images, model weights, feature caches and serialized joblib models are excluded until ownership, licensing, and privacy implications are assessed.
