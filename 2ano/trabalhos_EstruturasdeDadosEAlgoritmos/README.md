# Data Structures & Algorithms II (EDA2) — Algorithmic Problem Solutions

A curated collection of practical assignments developed for the **Data Structures and Algorithms II (EDA 2)** curriculum at the University of Évora. The repository centers on solving computationally demanding algorithmic problems through advanced data structures, combinatorial optimization, graph traversals, and maximum network flow algorithms.

Each implementation is benchmarked against rigorous time- and space-complexity constraints on large-scale datasets.

---

## Tech Stack & Tools

### Platform & Core Technologies
![Java](https://img.shields.io/badge/java-%23ED8B00.svg?style=for-the-badge&logo=openjdk&logoColor=white)
![Git](https://img.shields.io/badge/git-%23F05033.svg?style=for-the-badge&logo=git&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black)

---

## Repository Projects & Algorithmic Breakdown

The repository is structured into three self-contained modules, each featuring complete Java source implementations, problem specifications, and technical complexity reports:

| Project | Problem Domain | Algorithmic Core | Complexity / Target Scale |
| :--- | :--- | :--- | :--- |
| **[Assignment 1] The Dream Factory** | Resource packing & waste minimization under arrival-order constraints. | Bottom-Up Dynamic Programming & Binary Search | Scales to 100,000 items with optimal time bounds. |
| **[Assignment 2] Palm Island Neighbours** | Tree topology diameter (maximum shortest path between any two nodes). | Graph Theory & Double Breadth-First Search (BFS) | Linear time complexity: $\mathcal{O}(V + E)$. |
| **[Assignment 3] Card Exchange** | Circular asset exchange feasibility and matching validation. | Network Flow & Edmonds-Karp Algorithm (Max Flow) | Polynomial time bounded by residual network capacity. |

---

## Deep Dive: Problem Formulations & Strategies

### 1. The Dream Factory — Dynamic Programming
* **Problem**: Minimize wasted container capacity when packing heterogeneous "dreams" arrived in a strict FIFO sequence into fixed-capacity numerical bins.
* **Algorithmic Strategy**: Utilized a bottom-up Dynamic Programming table coupled with binary search lookups to identify optimal state transitions, preventing redundant recomputations across inputs up to $N = 100{,}000$.

### 2. Palm Island Neighbours — Tree Diameter
* **Problem**: Compute the longest shortest path (graph diameter) separating two inhabitants on an acyclic topological island network.
* **Algorithmic Strategy**: Executed two consecutive BFS passes—the first locating the furthest vertex from an arbitrary root, and the second measuring the maximal path from that extreme point to yield the exact tree diameter in linear time $\mathcal{O}(V + E)$.

### 3. Card Exchange — Maximum Network Flow
* **Problem**: Verify the existence of a valid circular trade loop where every festival participant acquires a coveted card without deficit.
* **Algorithmic Strategy**: Modeled the problem as a bipartite-style flow network augmented with a source $S$ and sink $T$. Applied the Edmonds-Karp algorithm (BFS-based augmenting paths); an optimal maximum flow equal to total participant count confirms feasibility.

---

## Repository Structure

```text
├── Trabalho1/                    # The Dream Factory (Dynamic Programming)
│   ├── Main.java
│   └── relatorio.pdf
├── Trabalho2/                    # Palm Island Neighbours (Double BFS / Tree Diameter)
│   ├── Main.java
│   └── relatorio.pdf
└── Trabalho3/                    # Card Exchange (Edmonds-Karp / Network Flow)
    ├── Main.java
    └── relatorio.pdf
