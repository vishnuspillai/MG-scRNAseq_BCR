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


---

## 🔄 Workflow Summary

### 1️⃣ **Seurat Preprocessing**
- Input: CD45⁺ thymic B cells from GSE233180.
- Filters applied, clusters identified, and `Bcell_type` assigned using marker-based annotation.
- Output: `Bcells_annotated_seurat_obj.rds`

### 2️⃣ **BCR Integration via Platypus**
- 12 BCR CSVs parsed from GEO.
- Barcode cleaning, sample naming standardized.
- `combineBCR()` and `VDJ_df` merged with Seurat object.
- Clonotypes stored under `raw_clonotype_id`, `clone_size`.

### 3️⃣ **Clonal Overlay and Expansion**
- Clonotype UMAP overlay based on `clone_size`.
- Expansion statistics by B cell subtype saved to CSV.

### 4️⃣ **Differential Gene Expression (DEG)**
- DEGs between **Expanded vs Unique clones** for each `Bcell_type`.
- Top 10 genes used for expression heatmaps.
- DEG CSVs saved per subtype.

### 5️⃣ **GO Enrichment Analysis (gProfiler2)**
- GO:BP terms retrieved for upregulated DEGs using `gost()`.
- Barplots and CSVs generated per B cell subtype.

### 6️⃣ **V Gene Usage & SHM Entropy**
- Plots for top V genes per subtype and shared VJ usage matrix.
- SHM entropy calculated across subtypes.
- All results saved in `results/tables/` and `figures/v_gene/`.

### 7️⃣ **Clonal Sharing Analysis**
- Clonotype overlap matrix → heatmap.
- UpSet plot for expanded clones across samples.
- Graph network using `igraph` and `ggraph`.

---

## 📦 Dataset Details

- **GEO Accession**: [GSE233180](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE233180)
- **Patients**: 12 EOMG (AChR+), 10 females, 2 males.
- **Modality**: 10x Genomics V(D)J + GEX (5′)

---

## 🧠 Future Directions

- [ ] Clonotype-specific marker discovery (`FindMarkers` per top clone)
- [ ] Pseudotime trajectory (Slingshot or Monocle)
- [ ] TCR integration (if dataset permits)
- [ ] Report/Quarto rendering

---

## 👨‍🔬 Author

**Vishnu S. Pillai**  
Bioinformatician | Immunogenomics | AI for Biology  
🔗 [GitHub](https://github.com/vishnuspillai)

---

## 📜 Citation

If you use this pipeline or refer to its results, please cite the corresponding GEO dataset (GSE233180) and acknowledge this repository.



## 📄 License

MIT License. See [LICENSE](LICENSE) for details.
