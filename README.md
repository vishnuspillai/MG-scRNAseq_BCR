# MG-scRNAseq_BCR

This repository contains a structured single-cell RNA-seq (scRNA-seq) and B-cell receptor (BCR) analysis workflow using the GSE233180 dataset. The analysis focuses on dissecting B cell heterogeneity and BCR clonal architecture in **Myasthenia Gravis (MG)** thymic tissue, using samples from 12 AChR-Ab+ early-onset MG patients.

---

## 📦 Project Structure

```
MG-scRNAseq_BCR/
├── data/
│   ├── scrna/          # Raw .h5 files per sample (MG1–MG12)
│   ├── bcr/            # BCR CSVs (filtered_contig_annotations)
│   └── processed/      # Seurat objects after filtering, annotation, clone mapping
├── results/
│   ├── figures/
│   │   ├── umaps/      # UMAPs by cluster and B cell type
│   │   ├── heatmaps/   # Marker gene heatmaps
│   │   └── clones/     # BCR clone overlay plots
│   └── tables/         # Marker gene lists, clone statistics
├── 01_scripts/         # Preprocessing, clustering, annotation
├── 02_scripts/         # BCR integration, clonal analysis
└── README.md           # This file
```

---

## 🔍 Dataset Summary

- **GEO Accession**: [GSE233180](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE233180)
- **Samples**: 12 MG thymic CD45+ scRNA-seq datasets
- **Modality**: 10x Genomics 5’ scRNA + V(D)J
- **Focus**: B cell subtype classification and clonal diversity analysis

---

## 🧪 Analysis Pipeline

### ✅ Step 1: B cell Subclustering
- Input: `.h5` files from 10x
- Tools: `Seurat`, `tidyverse`
- Output:
  - Clustered and normalized Seurat object
  - DE marker identification
  - Manual annotation into B cell subtypes

### ✅ Step 2: BCR Clone Mapping
- Input: `filtered_contig_annotations.csv` per sample
- Tools: `scRepertoire`, `Seurat`
- Output:
  - Clone overlay on UMAP
  - Clonal expansion statistics per subtype

### 🔄 Step 3: [Upcoming]
- B cell lineage inference and clone tracking
- Pseudotime integration (optional)
- Cross-patient clone overlap analysis

---

## 📚 Key Technologies

- `Seurat` v5 (H5-based layering system)
- `scRepertoire` for BCR processing
- `ggplot2`, `dplyr`, `cowplot`, `patchwork`
- File-safe coding with fixed directories

---

## 🧠 Author

**Vishnu S. Pillai**  
Bioinformatician, Single Cell + Immunology + Epigentics 
📍 Kerala, India  
🧬 GitHub: [@vishnuspillai](https://github.com/vishnuspillai)

---

## 📄 License

MIT License. See [LICENSE](LICENSE) for details.
