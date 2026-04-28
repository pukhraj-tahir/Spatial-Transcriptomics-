# 02 — Visium Fluorescence Image Analysis

## Overview
This notebook extends the spatial workflow into **image-based analysis** using **Squidpy** on a **Mouse Brain Visium** dataset with a fluorescence (DAPI) image. The focus is on nucleus segmentation, extraction of image-derived features, and correlating those features with gene expression clusters.

**Dataset:** 10x Genomics Mouse Brain (Visium + DAPI fluorescence)  
**Platform:** Google Colab  
**Key Libraries:** `squidpy`, `scanpy`, `scikit-image`

---

## Workflow

### 1. Spatial Cluster Visualization
Leiden clusters from transcriptomic data overlaid on the fluorescence image, establishing the baseline gene expression landscape of the mouse brain tissue.

![Spatial Clusters](results/spatial_clusters.png)

---

### 2. Nucleus Segmentation
The DAPI channel is segmented using the **watershed algorithm** from `scikit-image`. The segmentation mask is compared side-by-side with the raw fluorescence image to assess quality.

- **Left:** Raw DAPI fluorescence image
- **Right:** Watershed segmentation mask (each nucleus = unique color)

![Segmentation Comparison](results/segmentation_comparison.png)

---

### 3. Image Feature Extraction & Correlation with Gene Expression
Morphological and texture features are extracted per Visium spot from the fluorescence image (e.g., mean intensity, texture summary statistics). These image features are then compared against the transcriptomic cluster annotations to reveal whether morphology and gene expression are correlated.

![Image Features vs Clusters](results/image_features_vs_clusters.png)

---

## Key Concepts
| Concept | Description |
|---|---|
| DAPI staining | Fluorescent dye that binds DNA; marks all nuclei |
| Watershed segmentation | Algorithm that treats pixel intensities as a topographic map and "floods" from seed points to delineate boundaries |
| Image features | Quantitative descriptors extracted from image patches (intensity, texture, histogram statistics) |
| Multi-modal integration | Combining image-derived features with RNA-seq data per spot |

## Dependencies
```bash
pip install scanpy squidpy scikit-image igraph leidenalg
```
