# Ouri Board Game Engine — Strategy Game Implementation (C)

Terminal-based engine for the traditional mancala-variant board game "Ouri", engineered in procedural C. Implements complete game state loops, rule enforcement algorithms (sowing mechanics, chain-reaction captures, and boundary skipping), automated engine-opponent logic, and file-based state serialization.

Developed as part of the Programming I (Programação 1) curriculum at the University of Évora (Academic Year 2023/2024).

---

## Tech Stack & Tools

### Platform & Core Technologies
![C](https://img.shields.io/badge/c-%2300599C.svg?style=for-the-badge&logo=c&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black)
![Git](https://img.shields.io/badge/git-%23F05033.svg?style=for-the-badge&logo=git&logoColor=white)

---

## Game Rules & System Architecture

The game is modeled around a 14-pit board representation: 12 active playing pits (6 per player) and 2 score storehouses (*depósitos*). The primary objective is to capture 25 out of the 48 total seeds.

| Component / Subsystem | Implementation File | Technical Role & Mechanism |
| :--- | :--- | :--- |
| **Core Game Loop** | `ouri.c` | Coordinates turn-taking, input parsing, victory validation, and board rendering. |
| **Sowing Engine** | `ouri.c` | Counter-clockwise seed distribution routines, handling large pit skips (>11 seeds). |
| **Capture Logic** | `ouri.c` | Backward chain-reaction verification for valid capturing states (2 or 3 seeds). |
| **Game Modes** | `ouri.c` | Player vs. Player (PvP) and basic automated bot opponent (Player vs. Engine). |
| **State Persistence** | `ouri.c` | CLI argument parsing and I/O serialization for reading/writing board matrices to `.txt`. |

---

## Key Technical Decisions

* **Procedural Board State Representation**: Modeled the 14-pit circular board using static arrays with index-arithmetic wrapping, minimizing memory allocation overhead and ensuring cache locality.
* **Complex Sowing & Rule Enforcement**:
  * **The "12-Rule" (Large Pits)**: Designed distribution tracking to skip the origin pit whenever a hand contains 12 or more seeds, ensuring strict compliance with official Ouri rules.
  * **Single-Seed Restrictions**: Enforced movement limitations preventing non-essential single-seed moves when higher-stack alternatives are available.
  * **Chain-Reaction Captures**: Built recursive/iterative check routines evaluating contiguous opposing pits backwards to award valid 2-seed and 3-seed captures.
* **Stateless Save & Load Pipeline**: Utilized standard C file stream APIs (`fopen`, `fscanf`, `fprintf`) to serialize and restore board layouts directly via file arguments during CLI invocation.

---

## Repository Structure

```text
├── ouri.c                        # Core game logic, rule verification, and CLI rendering
├── Relatório P1.pdf              # In-depth technical report and algorithmic explanations
├── tabuleiro_exemplo.txt         # Optional saved state file for game resumption testing
└── README.md                     # Project documentation
