# Unit I: OS Revision Cheat Sheet

A high-speed revision guide for exam prep. Study this sheet to review key formulas, memorize tricks, resolve confusion zones, and avoid common exam traps.

---

## ⚡ 1. Critical Formulas Card

### CPU Scheduling Calculations
*   **Turnaround Time (TAT)**: Total duration from process arrival to termination.
    $$\text{TAT} = \text{Completion Time (CT)} - \text{Arrival Time (AT)}$$
*   **Waiting Time (WT)**: Time spent sitting in the ready queue.
    $$\text{WT} = \text{Turnaround Time (TAT)} - \text{Burst Time (BT)}$$
*   **Response Time (RT)**: Time from arrival to first CPU execution.
    $$\text{RT} = \text{Time of first CPU response} - \text{Arrival Time (AT)}$$

### Memory Address Translation
*   **Logical Address Space (LAS) Size** = $2^L$ bytes (where $L$ is the number of logical address bits).
*   **Physical Address Space (PAS) Size** = $2^P$ bytes (where $P$ is the number of physical address bits).
*   **Page Size (PS)** = **Frame Size** = $2^d$ bytes (where $d$ is the offset bits).
*   **Number of Pages** = $\text{LAS Size} / \text{Page Size} = 2^{L-d}$.
*   **Number of Frames** = $\text{PAS Size} / \text{Frame Size} = 2^{P-d}$.

### Effective Memory Access Time (EAT)
*   **EAT with TLB**: Let $h$ be the TLB hit ratio, $t$ be the TLB access time, and $m$ be the main memory access time.
    $$\text{EAT} = h \times (t + m) + (1 - h) \times (t + 2 \times m)$$
    *(Note: On a TLB miss, we search the TLB ($t$), read the page table from memory ($m$), and then access the target physical memory address ($m$), totaling $t + 2m$.)*
*   **EAT with Demand Paging**: Let $p$ be the page fault rate, $m$ be the memory access time, and $S$ be the page fault service time.
    $$\text{EAT} = (1 - p) \times m + p \times S$$

---

## 📊 2. High-Yield Comparison Tables

### Kernel Architectures
| Feature | Monolithic Kernel | Microkernel |
| :--- | :--- | :--- |
| **Space** | Single address space (Kernel space) | Two spaces (Minimal kernel, services in User space) |
| **Speed** | **Fast** (direct function calls) | **Slow** (messages sent via IPC & context switches) |
| **Fault Tolerance**| Low (one driver crash takes down entire OS) | High (faulty driver runs as a server, can be restarted) |
| **Examples** | Linux, macOS (BSD-like XNU), Unix | MINIX, QNX, L4 |

### Synchronization: Mutex vs. Semaphore
| Feature | Mutex | Binary Semaphore | Counting Semaphore |
| :--- | :--- | :--- | :--- |
| **Core Concept** | A lock mechanism. | A signaling flag. | A resource counter. |
| **Ownership** | **Yes** (Only the thread that locks can unlock). | **No** (Any thread can wake up a blocked thread).| **No**. |
| **Values** | Boolean state (Locked/Unlocked). | $\{0, 1\}$. | Range of integers $(-\infty, \infty)$ or $[0, N]$. |
| **Use Case** | Protecting a single critical section. | Triggering signals between threads. | Managing a pool of $N$ identical resources. |

### Memory Management: Paging vs. Segmentation
| Feature | Paging | Segmentation |
| :--- | :--- | :--- |
| **Block Size** | Fixed-sized blocks (Pages/Frames). | Variable-sized blocks (Segments). |
| **User View** | Invisible to user/programmer. | Aligns with user's perspective (Functions, Stacks, Heap).|
| **Fragmentation**| **Internal Fragmentation** only (in last page). | **External Fragmentation** only (scattered free blocks). |
| **Page Table** | Indexed by Page Number ($p$). | Contains Segment Base Address & Limit. |

---

## 🧠 3. Memory Tricks & Mnemonics

*   **Operating System Types**: **BT-DRE**
    *   **B**atch, **T**ime-sharing, **D**istributed, **R**eal-time, **E**mbedded.
*   **Process States**: **NR-RWT**
    *   **N**ew, **R**eady, **R**unning, **W**aiting, **T**erminated.
*   **Coffman Conditions (Deadlock)**: **M-HNC** (pronounce: "M-Hance")
    *   **M**utual Exclusion, **H**old and Wait, **N**o Preemption, **C**ircular Wait.
*   **RAID Levels**:
    *   **RAID 0**: Z**ero** Fault Tolerance (Striping).
    *   **RAID 1**: **One-to-One** Copy (Mirroring).
    *   **RAID 5**: **Five-sided** Balance (Striping + Distributed Parity).
    *   **RAID 6**: **Double** Parity (Can survive 2 disk failures).

---

## 🚨 4. High-Risk Confusion Zones

### 1. User Mode vs. Kernel Mode
*   **Confusion**: Does a mode switch mean a context switch?
*   **Reality**: **No!** A mode switch (User $\to$ Kernel) is cheap. It happens during a system call within the same process context. A context switch (Process A $\to$ Process B) is expensive because it swaps CPU registers, page tables, and invalidates hardware caches.

### 2. Thread vs. Process Memory Sharing
*   **Confusion**: What do threads share?
*   **Reality**:
    *   **Shared**: Code section, Data section (global variables), Heap, Open files.
    *   **Private**: Thread ID, Program Counter (PC), Register state, Stack (local variables).

### 3. Banker's Algorithm: Prevention vs. Avoidance
*   **Confusion**: Does the Banker's algorithm prevent deadlock?
*   **Reality**: **No**. Banker's is a **Deadlock Avoidance** algorithm. It dynamically monitors resource requests and checks for safety. **Deadlock Prevention** refers to static design choices that break the Coffman conditions (e.g., spooling to break mutual exclusion).

---

## ⚠️ 5. Traps & Mistakes to Avoid in Exams

*   **Page Replacement Calculations**: When calculating FIFO page faults, watch out for **Belady's Anomaly**. Do NOT assume that increasing frame count automatically reduces page faults unless it's LRU or Optimal.
*   **Round Robin Quantum Limits**: If Time Quantum $\to \infty$, Round Robin becomes **FCFS**. If Time Quantum $\to 0$, it becomes **Processor Sharing** (infinite context-switching overhead).
*   **Ready state transition**: A process in the *Waiting/Blocked* state **cannot** transition directly to the *Running* state. It must go to the *Ready* state first to wait for the scheduler's dispatch.
*   **Semaphores blocking**: Remember that a negative semaphore value indicates the number of processes currently blocked and waiting on that semaphore.
