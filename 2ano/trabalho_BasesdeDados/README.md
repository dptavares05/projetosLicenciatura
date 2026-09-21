# Pastry Recipe & Social Member Management System (SQL)

Relational database model and complex query suite engineered to govern a community-driven culinary platform. Designed to manage member social graphs (recursive friendships), categorized pastry recipes, ingredient-level unit cost aggregation, and preparation logs with qualitative sensory ratings.

Developed as part of the Databases (Bases de Dados) curriculum at the University of Évora.

---

## Tech Stack & Tools

### Platform & Core Technologies
![SQL](https://img.shields.io/badge/sql-%2300758F.svg?style=for-the-badge&logo=mysql&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/postgresql-%23316192.svg?style=for-the-badge&logo=postgresql&logoColor=white)
![Git](https://img.shields.io/badge/git-%23F05033.svg?style=for-the-badge&logo=git&logoColor=white)

---

## Relational Schema & Entity Overview

The schema models an interactive culinary social network, balancing entity normalization against analytical query performance:

| Entity / Table | Conceptual Relationship | Role & Key Attributes |
| :--- | :--- | :--- |
| **Membros (Members)** | Core Entity | User accounts with demographic metadata (birth date, nationality, profile records). |
| **Amizades (Friendships)** | Recursive Self-Referencing Relation | Directed/undirected graph representation linking members to peers. |
| **Doces & Ingredientes** | Many-to-Many via Composition Junction | Recipe catalog detailing genres, quantities, and ingredient unit costs. |
| **Fez (Preparations Log)** | Event History Junction | Historical execution log tracking recipe creation, preparation duration, and visual/flavor scores. |

---

## Core Analytical Capabilities & Business Logic

* **Dynamically Calculated Cost Modeling**: Aggregates variable recipe ingredient costs on the fly via composite joins, multiplying individual component quantities by unit pricing.
* **Sensory Quality & Member Ranking**: Multi-attribute aggregation queries determining top creators based on cumulative recipe outputs and average sensory scores (taste and presentation metrics).
* **Advanced Set & Relational Filtering**:
  * Exclusion queries identifying members who have never incorporated specific target ingredients (e.g., Vanilla).
  * Relational division and set containment queries to identify users who share an identical set of mutual friends with a given member.

---

## Key Technical Decisions

* **Relational Algebra Foundations**: Designed and verified complex query execution plans using formal Relational Algebra expressions before SQL implementation, ensuring minimal intermediate Cartesian products.
* **Strict Referential Integrity**: Configured foreign key cascades, unique pairs, and primary key constraints across recursive associations and multi-attribute relationship tables (`Fez`).
* **Advanced DDL & DML Optimization**: Implemented nested subqueries, correlated existence checks (`EXISTS` / `NOT EXISTS`), and aggregation filters (`GROUP BY`, `HAVING`) to solve real-world domain requirements cleanly.

---

## Repository Structure

```text
├── Criação da Base de Dados.txt     # DDL script defining table structures, keys, and relational constraints
├── Resposta as perguntas em SQl.txt # DML script containing mock datasets (INSERTs) and analytical queries
├── Relatório Base de Dados.pdf      # Comprehensive technical report with relational algebra derivations
└── README.md                        # Project documentation
