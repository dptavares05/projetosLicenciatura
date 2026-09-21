# Guru WordGame — Word Puzzle Game Engine (Java)

Console-based word puzzle game engine (inspired by Word Connect mechanics) developed in pure Java. Challenges players to discover valid vocabulary permutations from constrained letter sets across sequential difficulty levels, featuring dictionary validation, state persistence, in-game economies, and a level editor.

Developed as part of the Programming II (Programação II) curriculum at the University of Évora.

---

## Tech Stack & Tools

### Platform & Core Technologies
![Java](https://img.shields.io/badge/java-%23ED8B00.svg?style=for-the-badge&logo=openjdk&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black)
![Git](https://img.shields.io/badge/git-%23F05033.svg?style=for-the-badge&logo=git&logoColor=white)

---

## Game Architecture & Core Mechanics

The game loop operates through a terminal interface driven by text streams, orchestrating gameplay state, user input parsing, and flat-file asset management:

| Component / Subsystem | Implementation File / Resource | Technical Role & Mechanism |
| :--- | :--- | :--- |
| **Game Engine & Loop** | `Guru.java` | Coordinates turns, input validation, scoring, hints, and UI rendering. |
| **Dictionary Validator** | `portuguese-large.txt` | In-memory lexicon checking ensuring vocabulary compliance. |
| **Level Database** | `ficheiro_niveis.txt` | Formatted level configurations, target solutions, and letter allocations. |
| **State Persistence** | `game_state.txt` | Serializes progression states, player coin balances, and level indexes. |
| **Creative Mode** | `Guru.java` | Interactive authoring tool allowing custom level synthesis and disk export. |

---

## Key Technical Decisions

* **Constant-Time Lexicon Lookups**: Ingested `portuguese-large.txt` into a `HashSet<String>` data structure to guarantee $\mathcal{O}(1)$ average-time complexity during dictionary validation queries.
* **Anagram & Character Frequency Constraints**: Implemented frequency-array counting algorithms to verify that submitted words match the exact character frequency quotas provided by the current level rack.
* **Persistent State Synchronization**: Leveraged `BufferedReader` and `PrintWriter` for structured, atomic serialization and deserialization of player game states (`game_state.txt`), enabling seamless pause-and-resume workflows.
* **Dynamic Level Manipulation**: Used `ArrayList` collections to handle dynamic sizing and mutation of letter racks, level targets, and submitted word sets across gameplay cycles.

---

## Repository Structure

```text
├── Guru.java                     # Main entry point, game engine loop, and UI logic
├── portuguese-large.txt          # Extensive Portuguese dictionary dataset
├── ficheiro_niveis.txt           # Structured campaign level definitions
├── game_state.txt                # Game progress serialization file
├── relatorio.pdf                 # Comprehensive academic technical report
└── README.md                     # Project documentation
