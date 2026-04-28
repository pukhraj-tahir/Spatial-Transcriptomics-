# 03 — Visium H&E Spatial Statistics & Cell Communication

## Overview
This notebook focuses on **spatial statistics and ligand-receptor interaction analysis** using **Squidpy** on a **Mouse Brain Visium H&E** dataset. It moves beyond simple clustering to ask: *Which cell populations are spatially organized together? Which cell types communicate via secreted signals?*

**Dataset:** 10x Genomics Mouse Brain (Visium + H&E image)  
**Platform:** Google Colab  
**Key Libraries:** `squidpy`, `scanpy`, `igraph`, `leidenalg`

---

## Workflow

### 1. Spatial Cluster Visualization
Annotated brain regions (Hippocampus, Cortex, and others) overlaid on the H&E tissue image. Manual or automated annotations serve as the basis for all downstream spatial statistics.

![Spatial Clusters](results/spatial_clusters.png)

---

### 2. Neighborhood Enrichment Analysis
A permutation test that asks: *Are two clusters spatially closer to each other than expected by chance?*  
- **Red cells** in the heatmap = enriched co-localization (neighbors more often than random)  
- **Blue cells** = spatial avoidance  

This reveals the tissue architecture — e.g., which brain layers are adjacent.

![Neighborhood Enrichment](results/neighborhood_enrichment.png)

---

### 3. Co-occurrence Analysis — Hippocampus
Co-occurrence probability measures how the likelihood of finding the Hippocampus cluster near another cluster changes as a function of **spatial distance** (in µm). A peak at short distances indicates tight spatial coupling; a flat line indicates independence.

![Co-occurrence Hippocampus](results/co_occurrence_hippocampus.png)

---

### 4. Ligand-Receptor Interaction Analysis
Using the CellChat / NicheNet-style interaction database integrated in Squidpy, this plot shows statistically significant ligand-receptor pairs between pairs of spatially adjacent clusters — revealing potential paracrine signaling between brain cell populations.

![Ligand-Receptor Plot](results/ligrec_plot.png)

---

## Key Concepts
| Concept | Description |
|---|---|
| Neighborhood enrichment | Permutation test for spatial co-localization of cluster pairs |
| Co-occurrence score | Distance-dependent probability of two clusters being found together |
| Ligand-receptor analysis | Identifies putative cell-cell communication from gene expression |
| Spatial graph | Graph connecting spots by proximity (used for all neighborhood statistics) |

## Dependencies
```bash
pip install scanpy squidpy igraph leidenalg
```
