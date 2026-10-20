# Dataset documentation

## Internal images

3,000 original tea leaf images, six balanced classes (500 per class): `algal_spot`, `brown_blight`, `gray_blight`, `healthy`, `helopeltis`, `red_spot`.

- Train: 2,400 (400 per class)
- Validation: 300 (50 per class)
- Test: 300 (50 per class)

Splits were pre-existing in Google Drive. The author previously checked for duplicate images; this package has **not independently rerun** a duplicate or near-duplicate audit.

## External original images

66 original photographs spanning four represented labels: `algal_spot` (6), `brown_blight` (20), `healthy` (20), `helopeltis` (20). `gray_blight` and `red_spot` have no examples. Metrics are consequently limited to this subset and are sensitive to class imbalance.

## External generative-AI-edited images

66 edited counterparts of those same 66 external originals, produced by providing the source image and a text prompt to an AI-powered image editing feature in **CapCut** asking for improved visual quality while preserving the subject. The exact generative model, prompt text and processing parameters are **not documented**. Edits may affect visually diagnostic leaf characteristics. This set is *not* 66 additional independent images and should not be represented as a standard augmentation recipe.

## Redistribution and access

Source image licensing and redistribution permission were not established. No dataset files are bundled here. Researchers must obtain appropriate access/permissions and arrange folder paths before attempting to run the notebooks.
