# OppNetGuard — Opportunistic Network Messaging Simulation

Native Android mobile prototype engineered to simulate interface flows and state transitions for decentralized messaging in opportunistic networks (infrastructure-less, delay-tolerant environments). Designed to model the user experience and node behaviors required when communication relies entirely on intermittent peer encounters.

Developed as part of the Mobile Systems and Environments (SMA) curriculum at the University of Évora.

---

## Tech Stack & Tools

### Platform & Core Technologies
![Kotlin](https://img.shields.io/badge/kotlin-%237F52FF.svg?style=for-the-badge&logo=kotlin&logoColor=white)
![Android](https://img.shields.io/badge/Android-3DDC84?style=for-the-badge&logo=android&logoColor=white)
![Gradle](https://img.shields.io/badge/Gradle-02303A.svg?style=for-the-badge&logo=Gradle&logoColor=white)
![Git](https://img.shields.io/badge/git-%23F05033.svg?style=for-the-badge&logo=git&logoColor=white)

---

## System Overview & Simulated Roles

The application models dynamic peer-to-peer behaviors within ad-hoc, intermittent networks by simulating distinct node operating states through dedicated user interface layouts:

| Node Role | Screen / Interface Mode | Responsibility & Simulated Behavior |
| :--- | :--- | :--- |
| **Seed Node** | Seed Interface Mode | Acts as message originator; enables creation, configuration, and initial packet injection into the ad-hoc topology. |
| **Helper Node** | Relay Interface Mode | Acts as intermediary store-and-forward relay; visually tracks incoming packets and manages a local retention buffer awaiting encounters. |

---

## Key Technical Decisions

* **State-Driven UI Flows**: Modeled delay-tolerant network lifecycle transitions through decoupled view components, simulating real-world node discovery and transmission events.
* **Component Lifecycle Management**: Leveraged Android Activities/Fragments architecture to manage view hierarchies, navigation stacks, and volatile application states cleanly.
* **Minimal Overhead UX**: Designed clean UI layouts focused entirely on observability into packet buffers, operational modes, and simulated peer encounter states.

---

## Technical Scope & Constraints

> **Proof-of-Concept Notice**: This project was developed as a functional UI/UX prototype and node state simulator. Physical radio-layer transmissions (such as Wi-Fi Direct or Bluetooth Low Energy discovery) are emulated in software and not enabled at the hardware transport layer in this release.

---

## Getting Started

### Prerequisites
* **Android Studio**: Ladybug / Electric Eel or newer
* **Android SDK**: API Level 26+
* **JDK**: 17 or higher

### Build & Run Guide
1. **Clone the repository**:
   ```bash
   git clone [https://github.com/dptavares05/trabalho_redesOportunistas.git](https://github.com/dptavares05/trabalho_redesOportunistas.git)
   cd trabalho_redesOportunistas
   ```
