# Tea Leaf Disease Classification — VGG16 + Handcrafted Features + SVM

A comparative machine learning study of tea leaf condition classification using **VGG16 feature extraction**, complementary **Local Binary Pattern (LBP)**, **Gray-Level Co-occurrence Matrix (GLCM)**, or **HSV color features**, followed by a **Support Vector Machine (SVM)** classifier.

> **Academic research portfolio.** This repository presents the methods, original reported research findings, and lightly sanitized experimental notebooks. The notebooks are provided for methodological review and are not guaranteed one-click reproductions. See [Limitations](LIMITATIONS.md).

## Methods

1. Read RGB tea-leaf images and prepare model-specific inputs.
2. Extract pretrained ImageNet **VGG16** deep features using global average pooling (512 dimensions in the LBP implementation).
3. Extract handcrafted **LBP**, **GLCM**, or **HSV** features in three separate experiments.
4. Concatenate deep and handcrafted features, fit `StandardScaler` on training data, then search SVM hyperparameters on the validation set.
5. Refit the final SVM and scaler on training + validation; evaluate the held-out internal test set and external image sets.

## Datasets

| Dataset | Images | Covered classes | Description |
|---|---:|---:|---|
| Internal training | 2,400 | 6 | 400 per class |
| Internal validation | 300 | 6 | 50 per class |
| Internal test | 300 | 6 | 50 per class |
| External original | 66 | 4 | 6 algal spot, 20 each brown blight, healthy, and helopeltis |
| External AI-edited | 66 | 4 | Edited versions of the **same** 66 external images |

The six internal labels are `algal_spot`, `brown_blight`, `gray_blight`, `healthy`, `helopeltis`, and `red_spot`. `gray_blight` and `red_spot` have **no external reference images** in this evaluation. External samples are not balanced.

For dataset provenance, availability, and caveats, read [DATASET.md](DATASET.md). **Image files are not distributed in this repository**; redistribution rights were not established.

## Reported research results

| Combination | Internal test (approx.) | External original | External AI-edited |
|---|---:|---:|---:|
| VGG16 + LBP + SVM | 95% | 71% | 77% |
| VGG16 + GLCM + SVM | 95% | **76%** | 74% |
| VGG16 + HSV + SVM | 95% | 74% | **80%** |

These figures summarize the **results recorded in the original thesis experiments**. They describe the research findings, not benchmark claims independently verified using the published repository. External evaluation was limited to 66 images across four represented classes.

See [`results/reported_metrics.csv`](results/reported_metrics.csv).

## Notebooks

- [`01_vgg16_lbp_svm.ipynb`](notebooks/01_vgg16_lbp_svm.ipynb)
- [`02_vgg16_glcm_svm.ipynb`](notebooks/02_vgg16_glcm_svm.ipynb)
- [`03_vgg16_hsv_svm.ipynb`](notebooks/03_vgg16_hsv_svm.ipynb)

## Running / reproducibility

1. Open a notebook in **Google Colab**.
2. Mount your Google Drive and replace the `YOUR_DRIVE_PROJECT_ROOT` placeholder with your **own** research-data path.
3. Provide dataset folders expected by that notebook and verify class ordering.
4. Install dependencies as needed using [`requirements.txt`](requirements.txt); Colab default library versions may differ from the original research environment.
5. **Review cells before running.** Original research cells may split datasets, save caches or train models. Execution is not guaranteed reproducible without the original dataset, exact software versions, and cached artifacts.

Do not run all cells unattended on your only copy of the research data. This repository intentionally omits cached features, trained models, original and AI-edited photographs, and private Drive paths.

## Interpretation and limitations

The CapCut external editing step used **prompt-based generative image editing**, not a documented conventional brightness/contrast/sharpness transformation. The specific model, prompt history and settings are unavailable. Generative image editing can modify disease-specific details. The AI-edited set is an exploratory condition, **not an independently collected dataset**. The comparison between the top original and edited accuracies also involves different feature pipelines.

Read [LIMITATIONS.md](LIMITATIONS.md) before interpreting or citing the reported results.

## Project scope

Academic thesis research implemented in Python / Google Colab. This repository emphasizes the experimental comparison and transparent limitations rather than claiming a deployable production classifier.
