🧬 Disease–Gene Knowledge Graph using Neo4j

The Disease–Gene Knowledge Graph is an interactive Neo4j-based project designed to explore and visualize relationships between diseases, genes, drugs, and pathways. It provides a clear and interpretable representation of biological associations that can help in understanding disease mechanisms and potential therapeutic targets.

🧠 Project Overview

This project transforms biomedical data into a graph database where:

- Nodes represent entities such as Diseases, Genes, Drugs, and Pathways.

- Edges represent relationships like ASSOCIATED_WITH, TARGETS, or PART_OF.

By leveraging Neo4j and Cypher queries, the project allows users to:

- Visualize disease–gene–drug–pathway networks.

- Explore biological relationships through query-based insights.

- Extend the graph using real datasets like DisGeNET or DrugBank.

```
disease-gene-knowledge-graph/
│
├── inputs/
│   ├── Asthma_embeddings.csv
│   ├── disgenet_sample.csv
│   └── embeddings_node2vec.csv
│
├── outputs/
│   └── disease_association.csv
│
├── scripts/
│   ├── embeddings_node2vec.py
│   ├── graph_style.json
│   ├── link_prediction_demo.py
│   ├── load_neo4j.py
│   ├── nearest_neighbors.py
│   └── visualization_codes.txt
│
├── requirements.txt     # (Implied from Dockerfile, not shown explicitly)
├── docker_compose.yml
├── Dockerfile.txt
├── README.md
```
## 🚀 Getting Started

### Install dependencies

```bash
pip install -r requirements.txt
```

## 📦 Inputs

Source files and datasets used to build the knowledge graph:

- `inputs/disgenet_sample.csv` — Curated list of disease-gene associations (from DisGeNET).
- `inputs/Asthma_embeddings.csv` — Precomputed nearest-neighbor disease embeddings for Asthma.
- `inputs/embeddings_node2vec.csv` — Node2Vec embeddings for all diseases and genes (used for similarity and link prediction).

These files are required for ETL, graph construction, and downstream analyses.

### Launch Neo4j (Recommended: Docker Compose)

Start the Neo4j database locally using [Docker Compose](docker_compose.yml):

```bash
docker compose up neo4j
```

### Load sample data to Neo4j

Populate the Neo4j database from sample CSV:

```bash
python scripts/load_neo4j.py --csv inputs/disgenet_sample.csv --uri bolt://localhost:7687 --user neo4j --password neo4j1234
```

### Generate embeddings with Node2Vec

```bash
python scripts/embeddings_node2vec.py --uri bolt://localhost:7687 --user neo4j --password neo4j1234
```

### Find nearest diseases and candidate genes

```bash
python scripts/nearest_neighbors.py --disease Asthma --topk 5
python scripts/link_prediction_demo.py --disease Asthma --topk 5
```

#### [Optional] Run all scripts interactively

Explore other scripts in the `scripts/` directory for advanced analyses and visualization.

---

## 📊 Visualization

Open Neo4j Browser at [http://localhost:7474](http://localhost:7474) using user/password `neo4j/neo4j1234`.  
Use queries like:

```cypher
MATCH (d:Disease)-[r:ASSOCIATES_WITH]->(g:Gene)
RETURN d, r, g
LIMIT 100;
```

For more example queries, see [`scripts/visualization_codes.txt`](scripts/visualization_codes.txt).

---

## 📤 Outputs

Files generated during analysis and predictions:

- `outputs/disease_association.csv` — Matrix of disease–gene associations with scores (from Neo4j or ETL scripts).
- `outputs/nearest_disease.csv` — List of similar diseases for a target (e.g., Asthma), generated using embedding-based nearest neighbor search.
- `outputs/candidate_genes.csv` — Candidate genes for a disease, predicted by link prediction algorithms.

Output files provide actionable results and can be visualized using Neo4j Browser or imported to network analysis software.

---

## 📄 License

This project is licensed under the MIT License.

---

## About

An interactive Python/Neo4j-based network for exploring therapeutic and molecular relationships.  
Graph database integrates curated biomedical entities and edges, enabling deep query, visualization, and prediction of disease–gene–drug–pathway connections.

