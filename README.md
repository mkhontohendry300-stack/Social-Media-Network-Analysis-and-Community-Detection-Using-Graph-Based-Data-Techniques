#  Social Media Marketing — Community Detection

> A graph theory & network analysis research project
> Statistics South Africa 
> Cape Peninsula University of Technology — Introduction to Projects (PRJ360S)  
> Author: **Mkhonto Hendry Mike** | Student No: 221026908  
> Supervisor: Dr Vodha | April 2024

---

##  Project Overview

This project investigates **community detection in social media networks** using graph theory and Social Network Analysis (SNA). By analysing real-world social media data spanning the COVID-19 pandemic (2018–2023), the study compares three community detection algorithms to determine which best identifies meaningful communities within large-scale networks.

The goal is to understand how online communities form and grow over time, and how this insight can be applied to **social media marketing strategies**.

---

##  Research Objectives

1. Explain how SNA can be used to track changes in brand communities
2. Discuss the significance of SNA in shaping modern social media marketing tactics
3. Identify the limitations of SNA in comprehending brand communities
4. Compare community detection algorithms to determine which performs best
5. Measure the balance between community count and modularity score

---

##  Repository Structure

```
├── data/
│   └── covid19_social_media/      # Dataset from zenodo.org/records/4148941
├── scripts/
│   ├── girvan_newman.py           # Girvan-Newman community detection
│   ├── louvain.py                 # Louvain algorithm
│   ├── spectral_clustering.py     # Spectral clustering
│   └── centrality_measures.py     # Degree, betweenness, eigenvector centrality
├── figures/
│   ├── fig1_social_platforms_covid.png
│   ├── fig2_social_media_growth_2004_2018.png
│   ├── fig3_statistical_output.png
│   ├── fig4_girvan_newman_graph.png
│   ├── fig5_louvain_graph.png
│   └── fig6_spectral_clustering_graph.png
├── report/
│   └── PRJ360S_Community_Detection.pdf
└── README.md
```

---

##  Tools & Technologies

| Tool | Purpose |
|------|---------|
| **Python** | Core programming language |
| **NetworkX** | Graph creation and algorithm implementation |
| **SciPy / NumPy** | Numerical computation |
| **matplotlib** | Network and data visualizations |
| **NodeXL / Gephi** | SNA graph visualization |

---

##  Methodology

- **Dataset:** COVID-19 social media network dataset ([Zenodo](https://zenodo.org/records/4148941))
- **Period:** 2018–2023 (pre- and post-pandemic)
- **Network size:** 19,305 nodes | 58,060 edges | 2,515 communities detected
- **Primary metric:** Modularity (MOD) — measures the quality of community partitioning

### Graph Model

A social network is represented as a graph **G(V, E)**, where:
- **V** = set of nodes (users)
- **E** = set of edges (connections)
- Community detection finds a partition **C = {c₁, c₂, ..., cₖ}** grouping all nodes into k communities

---

## ⚙️ Algorithms Compared

### 1. Girvan-Newman Algorithm
Detects communities by iteratively removing edges with the highest **betweenness centrality**.
- Time complexity: O(E² × N)
- Modularity achieved: **0.395**

### 2. Louvain Algorithm
A fast, greedy modularity-optimisation algorithm introduced by Blondel et al. (2008). Widely used for large-scale network analysis.
- Modularity achieved: **0.395**

### 3. Spectral Clustering
Uses the **eigenvalues of the network's Laplacian matrix** (L = D - A) to partition nodes into communities.
- Modularity achieved: **0.0992**

---

##  Algorithm Comparison Results

| Algorithm | Modularity Score | Performance |
|-----------|-----------------|-------------|
| Girvan-Newman | 0.395 |  Good |
| Louvain | 0.395 |  Good |
| Spectral Clustering | 0.0992 |  Weak |

> **Conclusion:** Both the Girvan-Newman and Louvain algorithms outperformed Spectral Clustering on this dataset. Spectral Clustering struggled with the large, sparse network, producing a much weaker community structure. This contradicted the initial hypothesis that Spectral Clustering would perform best.

---

## 📈 Network Statistics (COVID-19 Dataset)

| Metric | Value |
|--------|-------|
| Number of Nodes | 19,305 |
| Number of Edges | 58,060 |
| Average Degree | 1,800 |
| Modularity | 0.435 |
| Communities Detected | 2,515 |

---

##  Centrality Measures (Sample Nodes)

| Node | Degree Centrality | Closeness Centrality | Betweenness Centrality | Eigenvector Centrality |
|------|:-----------------:|:--------------------:|:----------------------:|:----------------------:|
| 5    | 0.333 | 0.529 | 0.556 | 0.526 |
| 15   | 0.333 | 0.529 | 0.667 | 0.343 |
| 3    | 0.333 | 0.429 | 0.222 | 0.483 |
| 4    | 0.222 | 0.391 | 0.222 | 0.164 |

---

##  Getting Started

### Prerequisites

```bash
pip install networkx matplotlib scipy numpy
```

### Run Community Detection

```bash
# Girvan-Newman
python scripts/girvan_newman.py

# Louvain
python scripts/louvain.py

# Spectral Clustering
python scripts/spectral_clustering.py
```

### Example (Girvan-Newman)

```python
import networkx as nx
from networkx.algorithms.community import girvan_newman
from networkx.algorithms.community.quality import modularity

social_media_data = [
    (1, 3), (6, 3), (2, 4), (15, 4), (15, 5),
    (5, 6), (5, 3), (6, 7), (15, 8), (8, 9)
]

G = nx.Graph()
G.add_edges_from(social_media_data)

communities_generator = girvan_newman(G)
communities = next(communities_generator)

mod = modularity(G, communities)
print("Modularity:", mod)
```

---

##  Key Findings

- Social media communities **grew significantly** during COVID-19 lockdowns, as people moved online for connection and information
- The **Louvain Algorithm** is recommended for large-scale social network community detection due to its efficiency and competitive modularity
- **Spectral Clustering** underperformed on sparse, large datasets, suggesting it is better suited to smaller, denser networks
- Node **5** and **15** showed the highest betweenness centrality, identifying them as key bridges between communities

---

##  Key References

- Newman, M.E. & Girvan, M. (2004). Finding and evaluating community structure in networks.
- Blondel, V.D. et al. (2008). Fast unfolding of communities in large networks.
- Von Luxburg, U. (2007). A tutorial on spectral clustering.
- Alotaibi, N. & Rhouma, D. (2022). A review on community structures detection in time evolving social networks.

---

##  License

This project is for academic purposes at Cape Peninsula University of Technology and Statistics South Africa.


---

*Cape Peninsula University of Technology — Diploma in Mathematical Sciences, 2024*
