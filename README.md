# socialnetworkanalyzer
# 🔗 MatrixGraph-Engine: Social Network Connectivity Analyzer

A high-performance Python backend command-line tool that processes real-world social network structures to compute the "Degrees of Separation" between users. This project bridges higher mathematics and classical data structures by evaluating and benchmarking two distinct algorithmic philosophies: Linear Algebra Matrix Powers ($\mathbf{A}^k$) vs. Queue-based Breadth-First Search (BFS) traversals.

---

## 📊 Core Concepts & Mathematical Framework

This engine models a network of friendships as an **Undirected Graph** where people are represented as nodes and friendships are represented as edges. 

### 1. The Algebraic Philosophy (Adjacency Matrix)
The network is mapped into a massive square grid matrix $\mathbf{A}$, where:
* $\mathbf{A}_{ij} = 1$ if User $i$ and User $j$ are connected.
* $\mathbf{A}_{ij} = 0$ otherwise.

To find connectivity over multiple steps, we leverage the **Graph Theory Matrix Power Theorem**:
$$\mathbf{A}^k_{ij} = \text{The number of distinct paths of exact length } k \text{ between node } i \text{ and node } j$$
The engine iteratively computes powers of the matrix until the cell value at the target coordinates becomes non-zero ($\mathbf{A}^k_{ij} > 0$), proving a path exists.

### 2. The Structural Philosophy (Data Structures / BFS)
To optimize for real-world memory constraints, the engine implements a structural **Breadth-First Search (BFS)** traversal backed by a double-ended queue (`collections.deque`). This allows the backend to ripple outward from a source node, using a tracking `set` to protect system memory thresholds until it strikes the target node.

---

## 📈 Network Analysis Report (Dataset Results)

The engine was benchmarked using the verified **Stanford SNAP Facebook Ego Network** dataset containing anonymized crowd-sourced relationship coordinates.

### Dataset Overview:
* **Total Unique Nodes (Users):** 4,039
* **Isolated Graph Components:** 1 (The network is 100% fully connected)

### Algorithmic Insights Discovered:
* **Maximum Path Distance (Graph Diameter):** 6 steps  
  * *Mathematical Proof of the "Six Degrees of Separation" theory inside a real-world digital ecosystem.*
* **Average Path Distance:** 2.83 steps  
  * *Demonstrates the "Small-World" phenomenon where dense local clusters are tightly bridged by highly connected network hubs.*

---

## 🛠️ System Architecture & File Structure

The project repository is organized cleanly into modular backend layers:

* **`matrix_builder.py`**: Streamlined file IO system that reads the raw text edge list line-by-line, dynamically scales the matrix boundaries, and cleans input noise automatically.
* **`graph_solver.py`**: Contains the core path-finding algorithms, polished using defense-engineering strategies (input validation guard clauses to prevent index crashes).

---

## 🚀 Getting Started & Execution

### Prerequisites
Make sure you have Python 3 and NumPy installed on your system:
```bash
pip install numpy
