# 🌊 Automated Coastline Detection from Satellite Images using Edge Detection Algorithms

This repository presents a comparative evaluation of classical edge detection algorithms for extracting coastlines from Sentinel-2 satellite images. The work uses the **SWED (Satellite Water Edge Detection)** dataset and evaluates algorithms based on image quality metrics under noisy and blurred conditions.

---

## 📌 Objectives

- Implement and evaluate edge detection methods: Canny, Sobel, Prewitt, and LoG.
- Analyze robustness under Gaussian blur and noise distortions.
- Identify the most reliable metric (RMSE, PSNR, SSIM, FOM) for coastline detection accuracy.
- Visualize metric behavior per spectral band and detection threshold.

---

## 📂 Project Structure

```bash
├── canny_noise_blur.ipynb      # Canny edge detection under noise/blur
├── sobel_noise_blur.ipynb      # Sobel edge detection under distortions
├── sobel.ipynb                 # Clean Sobel evaluation
├── prewitt.ipynb               # Prewitt filter implementation
├── LoG.ipynb                   # Laplacian of Gaussian (LoG) method
├── test-image-issues.ipynb     # Troubleshooting image artifacts
├── comparison-metrics.ipynb    # Metric comparisons: RMSE, SSIM, PSNR, FOM
├── best_alg.ipynb              # Best algorithm and metric decision logic
├── utils.py                    # Preprocessing, evaluation, and visualization utilities
└── SWED/                       # Sentinel-2 SWED image-label directory (not uploaded due to size)
```

---

## Dataset – SWED

The **Satellite Water Edge Detection (SWED)** dataset includes:
* Download the full dataset from https://openmldata.ukho.gov.uk/#:~:text=The%20Sentinel-2%20Water%20Edges,required%20for%20the%20segmentation%20mask. 
* Multispectral Sentinel-2 satellite images with 12 bands.
* Corresponding binary label masks marking ground-truth coastline edges.
* Directory structure:

  ```
  SWED/
  ├── images/
  │   └── image_XXXX.tif
  └── labels/
      └── label_XXXX.tif
  ```

Each image is read and normalized, and corresponding masks are used to evaluate the accuracy of detected edges.

---

##  Evaluation Metrics

We use four evaluation metrics across all experiments:

| Metric   | Description                                                       |
| -------- | ----------------------------------------------------------------- |
| **RMSE** | Root Mean Square Error between predicted and reference edges      |
| **PSNR** | Peak Signal-to-Noise Ratio – evaluates image similarity           |
| **SSIM** | Structural Similarity Index – compares structural content         |
| **FOM**  | Pratt's Figure of Merit – precision-based metric for edge overlap |

FOM was found to be the most reliable in distorted settings.

---

##  How to Run

### 1. Install Dependencies

```bash
pip install numpy pandas matplotlib opencv-python scikit-image gdal pillow scipy
```

### 2. Prepare SWED Dataset

Place your SWED dataset as:

```
project-root/
└── SWED/
    ├── images/
    └── labels/
```

### 3. Run Notebooks

Run notebooks in this order for full pipeline:

1. `utils.py` – defines preprocessing and metric computation methods
2. `sobel.ipynb`, `prewitt.ipynb`, `LoG.ipynb` – clean baseline edge outputs
3. `canny_noise_blur.ipynb`, `sobel_noise_blur.ipynb` – noise/blur analysis
4. `comparison-metrics.ipynb` – metric visualizations across bands and thresholds
5. `best_alg.ipynb` – algorithm comparison and selection

---

## Visualizations

The pipeline produces plots of:

* Metric trends vs. thresholds and bands
* Metric comparisons across edge detection algorithms
* Annotated sample outputs showing metric values per threshold

---

## Dependencies

```text
numpy
pandas
matplotlib
opencv-python
scikit-image
gdal
pillow
scipy
```

---
