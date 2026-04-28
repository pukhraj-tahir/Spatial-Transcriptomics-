# 04 — Xenium Single-Cell Resolution Spatial Analysis

## Overview
This notebook represents the cutting edge of spatial transcriptomics — **true single-cell resolution** analysis using **10x Genomics Xenium** data and the **spatialdata** ecosystem. Unlike Visium (which captures 55 µm spots containing multiple cells), Xenium detects individual transcripts *in situ* with sub-cellular precision.

**Dataset:** 10x Genomics Human Lung Cancer (Xenium, 2 FOVs, 11,898 cells, 377-gene panel)  
**Platform:** Google Colab  
**Key Libraries:** `squidpy`, `spatialdata`, `spatialdata-io`, `spatialdata-plot`

---

## Workflow

### 1. Centrality Scores
Graph-theoretic centrality metrics computed per Leiden cluster on the spatial neighborhood graph. Three metrics are shown:

| Metric | Biological Meaning |
|---|---|
| **Closeness centrality** | How quickly a cluster can reach all others in the tissue graph — high = central location |
| **Average centrality** | Mean shortest path length to all other nodes |
| **Degree centrality** | Number of spatial neighbors — high = densely packed cluster |

These reveal which cell populations are spatially "hub-like" vs. peripheral in the tumor microenvironment.

![Centrality Scores](results/centrality_scores.png)

---

### 2. Co-occurrence Analysis
Distance-dependent co-occurrence probability starting from cluster 1, showing how spatial proximity to other clusters changes across increasing radii. This identifies which cell populations form tight spatial niches with the reference cluster.

![Co-occurrence](results/co_occurrence.png)

---

### 3. Single-Cell Spatial Cluster Map
Leiden clusters visualized at true single-cell resolution, with each dot representing one cell. The spatial organization of the human lung cancer tumor microenvironment is visible — tumor cells, immune infiltrates, and stromal populations each occupy distinct spatial territories.

![Spatial Clusters](results/spatial_clusters.png)

---

## Key Concepts
| Concept | Description |
|---|---|
| Xenium | In situ sequencing platform; detects transcripts at sub-cellular resolution |
| spatialdata | Python framework for handling multi-modal spatial omics data |
| Centrality scores | Graph metrics quantifying how central/connected each cluster is in the spatial graph |
| Moran's I | Spatial autocorrelation statistic — measures whether gene expression is spatially clustered |
| FOV | Field of View — the imaged region in Xenium experiments |

## Dependencies
```bash
pip install spatialdata spatialdata-io spatialdata-plot squidpy
```
