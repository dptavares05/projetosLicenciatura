# Image Denoising in RISC-V Assembly — Low-Level Digital Image Processing

Low-level digital image processing pipeline implemented in 32-bit RISC-V Assembly to filter noise from raw grayscale images (`.gray`). Implements discrete 2D spatial convolution windows using mean smoothing and median rank-order filtering with strict hardware register budgeting, memory layout management, and file I/O syscalls.

Developed as part of the Computer Architecture I (Arquitetura de Computadores I) curriculum at the University of Évora.

---

## Tech Stack & Tools

### Platform & Core Technologies
![Assembly](https://img.shields.io/badge/Assembly-RISC--V-blue?style=for-the-badge)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black)
![Git](https://img.shields.io/badge/git-%23F05033.svg?style=for-the-badge&logo=git&logoColor=white)

---

## Filter Implementations & Low-Level Mechanics

The program operates across raw byte arrays representing image pixel intensities, utilizing a 3x3 sliding spatial kernel to compute output values per pixel:

| Filter Type | Routine Label | Kernel / Algorithm Mechanism | Technical Advantage & Characteristics |
| :--- | :--- | :--- | :--- |
| **Mean Filter** | `filtro-media` | 3x3 uniform neighborhood summation and arithmetic division. | Uniform intensity smoothing; reduces high-frequency variance with bound-checking logic. |
| **Median Filter** | `filtro-mediana` | 9-byte neighborhood extraction sorted via register-level Insertion Sort. | Superior salt-and-pepper noise suppression while preserving critical structural edges. |

---

## Key Technical Decisions & Architecture

* **Register Budgeting & Calling Conventions**: Managed finite 32-bit RISC-V register files (`x0-x31`) manually across nested computational loops, minimizing stack spill overhead during kernel traversals.
* **In-Place Neighborhood Sorting**: Implemented an optimized low-level Insertion Sort directly in assembly to extract the median of the 9-byte sliding window without external library dependencies.
* **Explicit Boundary & Edge Checking**: Hardened coordinate arithmetic routines to check row and column boundaries, preventing out-of-bounds memory accesses around the perimeter of the image matrix.
* **Bare-Metal File I/O via Syscalls**: Handled file descriptors, raw binary stream reads, buffer allocations, and disk write operations directly via RARS runtime environment syscalls.
* **Dedicated Memory Buffering**: Maintained separated static data segments for input samples (`cat_noisy.gray`) and destination output buffers (`buffer_Saida`, `buffer_Saida2`) to isolate intermediate transformation states.

---

## Repository Structure

```text
├── filtro.asm                    # Core RISC-V source routine (I/O, filtering loops, sorting)
├── cat_noisy.gray                # Raw grayscale input benchmark image with injected noise
├── relatório.pdf                 # In-depth technical report, register analysis & visual outputs
├── enunciado.pdf                 # Official academic specification & requirements
└── README.md                     # Project documentation
