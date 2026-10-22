# A Framework for Automated Pathophysiological Pathway Synthesis and Mechanistic Disease Modeling Applied to Traumatic Brain Injury Associated Neurodegeneration

[![GitHub Repository](https://img.shields.io/badge/GitHub-doctor--shaheen%2FTBI--DNN-blue.svg)](https://github.com/doctor-shaheen/TBI-DNN)
[![Visualizer](https://img.shields.io/badge/Visualizer-Interactive%20DAG-emerald.svg)](DAG%20visualizer/index.html)
[![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)

Official publication repository and data library accompanying the study:
> **"A Framework for Automated Pathophysiological Pathway Synthesis and Mechanistic Disease Modeling Applied to Traumatic Brain Injury Associated Neurodegeneration"**  
> *Ahmed Shaheen, MD et al.*

---

## 🔬 Study Overview

Traumatic Brain Injury (TBI) is recognized as a major environmental risk factor for neurodegenerative dementias, including Alzheimer's Disease (AD), Chronic Traumatic Encephalopathy (CTE), Lewy Body Disease (LBD), Frontotemporal Dementia (FTD), and Vascular Dementia. However, isolating specific mechanistic cascades across disparate clinical and preclinical literature remains a formidable challenge.

This study reconstructs the multiscale and temporally evolving pathophysiological cascade linking TBI to chronic neurodegeneration using:
1. **Domain-Specific Transformer Embeddings (SapBERT)** combined with PCA and UMAP manifold learning.
2. **Unsupervised Density-Based Clustering (HDBSCAN)** identifying 68 clinically distinct clusters and 60 preclinical mechanistic clusters.
3. **Directed Acyclic Graph (DAG) Formalism** linking upstream biomechanical damage to intermediate vascular/inflammatory mediators and downstream proteostatic failure.
4. **An Interactive Visual Knowledge Library (DAG Visualizer)** enabling transparent exploration, validation, and reference traceability.

---

## 🚀 Interactive DAG Visualizer

To explore the disease networks interactively without installing any complex software:
1. Open the [`DAG visualizer/`](DAG%20visualizer/) directory.
2. Double-click [`index.html`](DAG%20visualizer/index.html) in your browser.
3. Features:
   - **Dual Evidence Modes**: Switch seamlessly between **Clinical Evidence** (68 clusters) and **Preclinical Evidence** (60 clusters).
   - **Interactive Graph Canvas**: Inspect nodes colored by biological location (Brain Tissue, Synapse, Mitochondria, Blood, CSF, etc.) and directed causal arrows.
   - **Traceability**: Click any edge to reveal its primary literature citations, confidence levels, and direct PubMed/DOI links.
   - **Export Options**: Export high-resolution publication PNGs or standardized JSON models.

For detailed documentation, see the [DAG Visualizer Guide](DAG%20visualizer/README.md).

---

## 📂 Repository Structure

```
├── DAG visualizer/
│   ├── index.html                   # Standalone interactive DAG viewer (Open in browser)
│   ├── dag_data.js                  # Pre-compiled database with all 128 DAG models & citations
│   ├── vis-network.min.js           # Offline graph layout and rendering engine
│   ├── README.md                    # Visualizer user instructions and schema specification
│   └── Light Weight Visualizer.docx  # Supplementary Word documentation
│
├── Figures/                         # High-resolution publication figures & path diagrams
│   ├── Figure 1 - Methods.png       # End-to-end computational pipeline
│   ├── Figure 2 - The Integrated Pathology.png # Unified causal cascade diagram
│   ├── Phase 1.png - Phase 11.png   # Mechanistic stage breakdowns (acute to chronic)
│   ├── complete clinical-evidence DAG diagram.svg / .png
│   ├── complete preclinical-evidence DAG diagram.svg / .png
│   ├── UMAP_2D_Scatter_All_Clusters_SapBERT.svg / .png
│   └── WordCloud_PCA_*.svg / .png
│
├── clinical paths meta data/        # Clinical literature evidence & network models
│   ├── clinical clusters description.xlsx # Cluster titles, definitions & reference indices
│   ├── JSON_DAGS/                   # 69 standardized JSON DAG files for clinical clusters
│   ├── normalized_JSON_batched_for_dag/ # Batched relation JSONs
│   ├── reference_clic.xlsx          # Full bibliographic reference database for clinical papers
│   └── dag_clic.xlsx                # Causal topology & backdoor status metrics
│
├── preclinical paths meta data/     # Preclinical literature evidence & network models
│   ├── preclinical clusters description.xlsx # Cluster titles, definitions & reference indices
│   ├── JSON_DAGS/                   # 61 standardized JSON DAG files for preclinical clusters
│   ├── normalized_JSON_batched_for_dag/ # Batched relation JSONs
│   ├── reference_preclic.xlsx       # Full bibliographic reference database for preclinical papers
│   └── dag_preclic.xlsx             # Causal topology & backdoor status metrics
│
├── PubMed Data/                     # Literature search strategies & source extraction data
│   ├── Search strategy & PICO.docx  # Exact PubMed search strings and Boolean queries
│   ├── flowchart_TBI.svg / .png     # PRISMA-compliant literature selection flow diagram
│   ├── clinical_pathways.xlsx       # Extracted clinical relationship triples with DOIs & text
│   ├── preclinical_pathways.xlsx    # Extracted preclinical relationship triples with DOIs & text
│   └── abstract-BrainInjur-set.txt.zip # Raw PubMed abstract corpora
│
├── TBI & Dementia Manuscript_v4.docx # Full study manuscript
├── appendix_.docx                   # Supplementary methodological appendix
└── README.md                        # Project root documentation
```

---

## 📊 Summary of Identified Clusters

| Metric | Clinical Literature | Preclinical Literature |
| :--- | :--- | :--- |
| **Identified Clusters** | 68 clusters (Cluster 0 to 67 + Noise) | 60 clusters (Cluster 0 to 59 + Noise) |
| **Embedding Model** | SapBERT (PubMedBERT fine-tuned) | SapBERT (PubMedBERT fine-tuned) |
| **Dimensionality Reduction**| PCA (80% variance) + UMAP (15D) | PCA (80% variance) + UMAP (15D) |
| **Clustering Algorithm** | HDBSCAN | HDBSCAN |
| **Causal Graph Output** | Directed Acyclic Graphs (JSON schema v3) | Directed Acyclic Graphs (JSON schema v3) |
| **Key Pathological Themes**| Axonal injury (NfL), tauopathy, BBB disruption, amyloid, microglial inflammation | Calcium dysregulation, mitochondrial fission, excitotoxicity, synaptic degradation |

---

## 📜 Citation & Attribution

If you utilize this repository, datasets, or the interactive DAG visualizer in your research, please cite:

```bibtex
@article{shaheen2026tbi,
  title={A Framework for Automated Pathophysiological Pathway Synthesis and Mechanistic Disease Modeling Applied to Traumatic Brain Injury Associated Neurodegeneration},
  author={Shaheen, Ahmed},
  journal={TBI-DNN Research Group},
  year={2026},
  url={https://github.com/doctor-shaheen/TBI-DNN}
}
```

---

## 📄 License

This repository is distributed under the **Creative Commons Attribution 4.0 International (CC BY 4.0)** license. You are free to share and adapt the material for any purpose, with appropriate credit to the authors.
