# Javascript-FacadeGNN

This repository contains a browser-based Graph Neural Network (GNN) implementation in JavaScript, featuring a facaded architecture for node-level, edge-level, and layer-level introspection and manipulation. The system is intended for technical inspection, experimentation, and step-by-step understanding of message-passing GNNs.

---

## Table of Contents

- [About](#about)
- [Features](#features)
- [Getting Started](#getting-started)
- [Basic Example](#basic-example)
- [Facade API](#facade-api)
- [Usage Notes](#usage-notes)
- [License](#license)

---

## About

Javascript-FacadeGNN is an interactive web application for experimenting with Graph Neural Networks (GNNs).  
It allows you to define custom graphs (nodes, edges, features), configure message-passing neural architectures, and observe/inspect all model states in real time via a built-in facade API.

It is designed for transparency and reproducible testing in a browser environment.

---

## Features

- Node, edge, and global graph configuration:
  - Adjustable number of nodes
  - Custom node features set by CSV, text, or manual entry
  - Custom edge lists (directed or undirected, optional self-loops)
- Model configuration:
  - Adjust feature size, hidden size, output size, and number of message-passing layers
  - Select activation function (`relu`, `leaky_relu`, `tanh`, `sigmoid`)
  - Choose loss function (MSE or BCE)
  - Control learning rate and training iterations
- Introspection and manipulation:
  - Facade API exposes raw weights, node embeddings (per layer), messages, gradients, adjacency, centralities, and more
  - Node/edge insertion, deletion, and mask/dropout toggling during runtime
  - Export and import of graph structures and trained weights
- Visualization:
  - Canvas-based drawing of node-link graphs
  - Node features and embeddings viewable per step
- Data import:
  - Manual, text, or CSV upload for node features, edges, and training targets
  - Batch training on a list of graphs/targets with CSV
- No dependencies: Single HTML/JS file runs in any modern browser

---

## Getting Started

### Requirements

- A current web browser (Chrome, Firefox, Edge, Safari, etc.)

### Install

1. Clone this repository:
    ```bash
    git clone https://github.com/matthewJamesAbbott/Javascript-FacadeGNN.git
    ```
2. Open `index.html` with your browser.

_No installation or server is required._

---

## Basic Example

To try a simple classification on a 5-node undirected cycle graph:

1. Open `index.html`
2. Under **Network Configuration**:
    - Feature Size: `3`
    - Hidden Size: `8`
    - Output Size: `2`
    - MP Layers: `2`
    - Activation: `relu`
    - Loss Function: `mse`
    - Learning Rate: `0.01`
3. Under **Graph Configuration**:
    - Number of Nodes: `5`
    - Edges (source,target per line):

        ```
        0,1
        1,2
        2,3
        3,4
        4,0
        ```
    - Node Features (paste in "Manual Node Features", one line per node):

        ```
        0.2,0.7,0.5
        0.8,0.1,0.4
        0.3,0.6,0.9
        0.5,0.2,0.8
        0.6,0.3,0.3
        ```

4. Enter **Target Output**: `1,0`
5. Set Training Iterations: `200`
6. Click **Train** or **Train with Progress**
7. Use the **GNN Facade API Explorer** to inspect node embeddings, readout output, or modify features.

---

## Facade API

All key network internals are accessible through the built-in UI controls in the **GNN Facade API Explorer** section.  
You may inspect or set:

- Node features and embeddings (per layer)
- Edge features
- Neighbors, adjacency and incidence data
- Per-layer message inputs and outputs
- Model weights, gradients, and optimizer stats
- Degree/betweenness/closeness centralities, PageRank
- Dropout/mask state for nodes/edges
- Training batch operations and outputs

Results of these queries and actions are shown in the Facade Output pane, or exported as CSV/JSON as applicable.

No external scripting is required; all controls are accessed from the application interface.

---

## Usage Notes

- Node and edge counts are restricted for browser performance.  
- For best results, use with graphs up to ~25 nodes; large graphs may be slow for training and visualization.
- All edits are made in-memory. To preserve or share experiments, use Export/Import features for models or graphs.
- No data leaves your browser.

---

## License

MIT License.  
Use, modify, share, or build upon for any purpose.

---

## Vercel Link

https://javascript-facade-gnn.vercel.app/

---
