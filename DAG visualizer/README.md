# TBI-DNN Interactive DAG Visualizer
**Disease Network Knowledge Library & Pathway Browser**  
*Supplementary Software for the TBI-to-Neurodegenerative Dementias (TBI-DNN) Study*

---

## Overview

The **TBI-DNN Interactive DAG Visualizer** is a lightweight, publication-grade web application developed to explore, inspect, and analyze directed acyclic graph (DAG) models generated from the biomedical literature. It reconstructs the multiscale causal cascades linking Traumatic Brain Injury (TBI) to chronic neurodegenerative dementias (Alzheimer's Disease, Chronic Traumatic Encephalopathy, Lewy Body Disease, Frontotemporal Dementia, and Vascular Dementia).

The visualizer provides complete traceability across:
- **68 Clinical Evidence Clusters** (SapBERT + HDBSCAN + causal triple DAGs)
- **60 Preclinical Evidence Clusters** (Animal models, molecular cascades, cellular mechanisms)
- **Traceable Evidence References** linked directly to PubMed / DOI identifiers.

---

## Quick Start Guide

### Option 1: Instant Local Launch (Zero Setup)
No web server or dependencies are required.
1. Navigate to the `DAG visualizer/` folder.
2. Double-click **`index.html`** to open it in any modern browser (Chrome, Safari, Firefox, Edge).
3. The visualizer loads completely offline with the pre-bundled `dag_data.js` database.

### Option 2: Run via Local HTTP Server
If you prefer running a local server:
```bash
# From within the "DAG visualizer" folder:
python3 -m http.server 8080

# Then open in your browser:
# http://localhost:8080
```

---

## Key Features & How to Use

### 1. Dataset Selection
At the top of the screen, toggle between:
- **Clinical Evidence**: 68 semantic clusters synthesizing human clinical observations, biomarkers (e.g., NfL, tau, amyloid), imaging (DTI, PET), and epidemiological cohorts.
- **Preclinical Evidence**: 60 semantic clusters detailing cellular pathways, blood-brain barrier disruption, neuroinflammation, microglial activation, and synaptic loss.

### 2. Exploring Clusters
- **Sidebar**: Browse all clusters sorted by ID. Each card displays the cluster number, title, node count, edge count, and a mechanistic summary definition.
- **Search**: Use the search bar at the top of the sidebar to filter clusters by keywords (e.g., `tau`, `microglia`, `BBB`, `inflammation`, `biomarker`).
- **Confidence Filter**: Filter edges by confidence ratings (`High`, `Medium`, or `All`).

### 3. Collapsible Sidebars & Canvas Workspace
To provide a clean, unobstructed view of complex DAG networks:
- **Collapsible Clusters Explorer (Left)**: Click the **`<`** icon in the sidebar header, the **`Clusters`** button in the top navigation, or press **`[`** on your keyboard. When collapsed, a floating **`Clusters`** tab on the left lets you re-open it instantly.
- **Collapsible Element Inspector (Right)**: Click the **`>`** icon in the inspector header, the **`Inspector`** button in the top navigation, or press **`]`** on your keyboard. When collapsed, a floating **`Inspector`** tab on the right allows quick restoration.
- **Auto-Expand on Selection**: Clicking any node or causal edge automatically expands the inspector if it was collapsed.
- **Minimizable Cluster Banner**: Click the **`−`** button on the floating cluster summary banner to minimize it into a compact pill.
- **Zen View (Maximize Canvas)**: Click **`Zen View`** in the header or press **`z`** on your keyboard to instantly collapse both sidebars for full-screen graph analysis and presentation.
- **Keyboard Shortcuts**:
  - **`[`** : Toggle Left Clusters Explorer
  - **`]`** : Toggle Right Element Inspector
  - **`z`** : Toggle Zen View (Full Canvas)
  - **`f`** : Fit Graph to Screen
  - **`Esc`** : Clear selection and reset view

### 4. Interactive DAG Canvas
- **Zoom & Pan**: Use the mouse scroll wheel or trackpad pinch to zoom. Click and drag empty space to pan.
- **Fit View**: Click the **Fit to Screen** icon in the floating toolbar to re-center the graph.
- **Layout Modes**:
  - **Hierarchical Left-to-Right (LR)** *(Default)*: Aligns upstream injury triggers on the left progressing to downstream pathological outcomes on the right.
  - **Hierarchical Top-to-Bottom (UD)**: Vertical cascade representation.
  - **Free Physics (Force-Directed)**: Organic spring-embedded layout with draggable nodes.
- **Biological Location Color Coding**: Nodes are automatically colored based on cellular and anatomical compartments (Brain Tissue, Blood, CSF, Synapse, Mitochondria, Astrocyte, Microglia, etc.). Click the **Info** button on the toolbar to toggle the color legend.

### 5. Element Inspection & Evidence Traceability
Click on any element in the graph to inspect its details in the right sidebar:
- **Clicking a Node**:
  - Displays the canonical label and ID.
  - Biological entity classification (Disease, Biomarker, Protein, Process, etc.).
  - Cellular/Tissue location compartment.
  - **UMLS Metathesaurus CUI** with a direct link to the NCI/NIH Metathesaurus browser.
  - Recorded synonyms and aliases.
- **Clicking a Causal Edge**:
  - Source and Target entities with causal arrow.
  - Causal Mechanism (e.g., `predisposes_to`, `activates`, `disrupts`, `impairs`).
  - Confidence rating badge (`High`, `Medium`, `Low`).
  - Detailed contextual explanation and contradictory evidence annotations.
  - **Traceable Evidence References**: Full citations of the primary literature supporting that specific relationship, complete with clickable **[PubMed ↗]** and **[DOI ↗]** links.

### 5. Exporting Figures & Data
- **Export PNG**: Captures the current graph view as a high-resolution PNG image suitable for figures and presentations.
- **Export JSON**: Downloads the standardized JSON DAG specification for the currently active cluster.
- **Load Custom JSON**: Click **Load Custom JSON DAG File...** at the bottom of the left sidebar to drag and drop or browse any custom DAG JSON file.

---

## Technical Architecture & File Structure

```
DAG visualizer/
├── index.html              # Core standalone single-page application
├── dag_data.js             # Pre-bundled database containing all 128 DAGs, descriptions & references
├── vis-network.min.js      # Offline Vis.js graph visualization engine
├── README.md               # Visualizer documentation and guide
└── Light Weight Visualizer.docx # Word-format documentation for journal supplementary submission
```

### JSON DAG Schema Specification
Each DAG file complies with the project's standardized schema:
```json
{
  "metadata": {
    "version": "3.0",
    "mode": "Unified_Strict",
    "node_count": 7,
    "edge_count": 6
  },
  "nodes": [
    {
      "id": "TraumaticBrainInjury",
      "label": "Traumatic Brain Injury",
      "type": "Disease",
      "location": "Brain_Tissue",
      "identifiers": { "UMLS_CUI": "C0006111" },
      "synonyms": ["TBI", "Head Injury"]
    }
  ],
  "edges": [
    {
      "source": "TraumaticBrainInjury",
      "target": "Dementia",
      "mechanism": "predisposes_to",
      "confidence": "High",
      "evidence_ref": [18, 61],
      "metadata": "Contextual description of causal mechanism..."
    }
  ]
}
```

---

## Browser Compatibility
Tested and compatible with:
- Google Chrome 90+
- Apple Safari 14+
- Mozilla Firefox 88+
- Microsoft Edge 90+

No plugins, extensions, or internet connection required for core offline usage.
