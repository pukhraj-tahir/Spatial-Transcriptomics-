# Spatial Transcriptomics Analysis — Scanpy & Squidpy

A collection of four fully documented Jupyter notebooks covering spatial transcriptomics analysis using **Scanpy** and **Squidpy**, progressing from foundational spot-level clustering to cutting-edge single-cell resolution analysis. Each notebook is designed to run on **Google Colab** using publicly available 10x Genomics datasets.

---

## Repository Structure

```
spatial-transcriptomics/
├── 01_scanpy_basic/
│   ├── notebook.ipynb          # Basic Scanpy spatial workflow
│   ├── README.md
│   └── results/                # Output plots
├── 02_squidpy_visium_fluo/
│   ├── notebook.ipynb          # Fluorescence image + segmentation
│   ├── README.md
│   └── results/
├── 03_squidpy_visium_hne/
│   ├── notebook.ipynb          # Spatial statistics & cell communication
│   ├── README.md
│   └── results/
├── 04_squidpy_xenium/
│   ├── notebook.ipynb          # Single-cell resolution Xenium analysis
│   ├── README.md
│   └── results/
└── README.md
```

---

## Notebooks at a Glance

### [01 — Basic Scanpy Spatial](./01_scanpy_basic/)
**Dataset:** Human Lymph Node (Visium)

The foundational spatial workflow: QC filtering, normalization, PCA, UMAP, Leiden clustering, marker gene identification, and spatial visualization of clusters and individual genes (CR2, COL1A2, SYPL1) overlaid on the H&E tissue image.

![Spatial Clusters NB1](01_scanpy_basic/results/spatial_clusters.png)

---

### [02 — Visium Fluorescence Image Analysis](./02_squidpy_visium_fluo/)
**Dataset:** Mouse Brain (Visium + DAPI fluorescence)

Nucleus segmentation of the DAPI channel using the watershed algorithm, extraction of morphological image features per spot, and correlation of those features with transcriptomic cluster identity.

![Segmentation NB2](02_squidpy_visium_fluo/results/segmentation_comparison.png)

---

### [03 — Visium H&E Spatial Statistics](./03_squidpy_visium_hne/)
**Dataset:** Mouse Brain (Visium + H&E)

Spatial statistics including neighborhood enrichment (which brain regions are spatially co-localized beyond chance), distance-dependent co-occurrence for the Hippocampus cluster, and ligand-receptor interaction analysis between spatially adjacent populations.

![Neighborhood Enrichment NB3](03_squidpy_visium_hne/results/neighborhood_enrichment.png)

---

### [04 — Xenium Single-Cell Spatial](./04_squidpy_xenium/)
**Dataset:** Human Lung Cancer (Xenium, 11,898 cells, 377 genes)

True single-cell resolution spatial analysis using the `spatialdata` ecosystem. Centrality scores reveal hub-like clusters in the tumor microenvironment; co-occurrence and Moran's I quantify spatial gene expression patterns.

![Spatial Clusters NB4](04_squidpy_xenium/results/spatial_clusters.png)

---

## Technology Stack

| Tool | Role |
|---|---|
| [Scanpy](https://scanpy.readthedocs.io/) | Core single-cell analysis (QC, normalization, clustering, UMAP) |
| [Squidpy](https://squidpy.readthedocs.io/) | Spatial statistics, graph construction, image features |
| [spatialdata](https://spatialdata.scverse.org/) | Xenium data handling (notebook 4) |
| [scikit-image](https://scikit-image.org/) | Nucleus segmentation via watershed |
| Leiden algorithm | Graph-based community detection |
| UMAP | Non-linear dimensionality reduction |

---

## Installation

```bash
# Notebooks 1–3
pip install scanpy squidpy igraph leidenalg scikit-image dask

# Notebook 4 (additional)
pip install spatialdata spatialdata-io spatialdata-plot
```

All notebooks are ready to run on **Google Colab** — datasets are downloaded automatically from 10x Genomics public servers within each notebook.

---

## Key Biological Concepts

- **Visium vs Xenium:** Visium captures 55 µm multi-cell spots with H&E or fluorescence imaging; Xenium achieves true single-cell resolution via in situ transcript detection
- **Spatial graphs:** Connect spots/cells by proximity to enable neighborhood statistics
- **Neighborhood enrichment:** Permutation test for spatial co-localization of cluster pairs
- **Co-occurrence:** Distance-dependent probability of two clusters being found together
- **Moran's I:** Spatial autocorrelation — measures whether gene expression is spatially clustered
- **Centrality metrics:** Graph-theoretic measures of how "hub-like" each cluster is in the tissue

---

## License
MIT License
