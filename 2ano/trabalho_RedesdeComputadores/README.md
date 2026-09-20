# Real-Time Chat & File Transfer System (UDP/TCP)

Client-server real-time communication platform engineered in C, designed for keystroke-by-keystroke message streaming without traditional submission triggers. Combines UDP datagrams for minimal-latency messaging with TCP stream sockets for reliable peer-to-peer file transfer, featuring concurrency management, sequence tracking, and timeout controls.

Developed as part of the Computer Networks curriculum at the University of Évora (Academic Year 2024/2025).

---

## Tech Stack & Tools
![C](https://img.shields.io/badge/c-%2300599C.svg?style=for-the-badge&logo=c&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black)
![Git](https://img.shields.io/badge/git-%23F05033.svg?style=for-the-badge&logo=git&logoColor=white)

---

## Architecture & Communication Protocols

The application leverages a hybrid transport architecture to optimize latency for interactive character streaming while preserving data integrity during bulk data exchange:

| Service / Channel | Protocol | Port Allocation | Responsibility & Behavior |
| :--- | :--- | :--- | :--- |
| **Messaging Engine** | UDP | `12345` (Server listener) | Low-latency, character-by-character transmission and session signaling. |
| **File Transfer Engine** | TCP | Dynamic (`20000–21000`) | Reliable, stream-oriented data exchange for authenticated file sharing. |
| **Session Control** | UDP | `12345` | Activity monitoring, keep-alives, and forced disconnect on idle timeouts. |

---

## Core Features

* **Keystroke-Level Real-Time Streaming**: Dispatches individual character buffers instantly over UDP, allowing connected users to observe live message construction.
* **Access Control & User Registry**: Mandatory registration and authentication pipeline with flat-file credential persistence stored in `contas.txt`.
* **Multi-Tier Routing & Messaging Channels**: Native support for global broadcasts (`[all]`) alongside private direct messages (`[dm]`) routed via server dispatch.
* **Dynamic Group Management**: Full group lifecycle operations (create, join, leave, kick, and dissolve by owner), with group memberships persisted in `groups.txt`.
* **Hybrid File Transfer Pipeline**: Handshake negotiation and metadata signaling handled via UDP, followed by direct stream transfer across dynamically assigned TCP ports.
* **Inactivity & Session Watchdog**: Proactive client liveness checks that terminate unacknowledged or idle client connections exceeding 60 seconds (`CLIENT_TIMEOUT`).
* **Datagram Reliability & Loss Accounting**: Explicit packet sequence numbering over UDP to quantify, log, and report datagram loss rates during periodic server checkpoint cycles.

---

## Key Technical Decisions

* **Hybrid Transport Layer**: Decoupled message broadcasting from file payloads, utilizing connectionless UDP for minimal latency and dedicating stream-oriented TCP sockets strictly to bulk transfers.
* **Low-Level Socket Multiplexing**: Managed network events, keyboard input, and client descriptors via POSIX socket APIs and I/O multiplexing primitives.
* **Dynamic Ephemeral Port Pools**: Implemented dynamic port discovery between ranges `20000` and `21000` to prevent port collisions during simultaneous file transfer sessions.
* **Defensive Packet Loss Tracking**: Compensated for native UDP unreliability by instrumenting packet headers with sequence numbers and tracking metrics directly on the server console.

---

## Getting Started

### Prerequisites
* **Compiler**: GCC / Clang
* **Environment**: POSIX-compliant OS (Linux recommended)

### Compilation
Compile both server and client source binaries using GCC:

```bash
# Compile Server
gcc -Wall -Wextra svFINAL.c -o server

# Compile Client
gcc -Wall -Wextra clFINAL.c -o client
