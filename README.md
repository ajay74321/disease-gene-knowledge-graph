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
