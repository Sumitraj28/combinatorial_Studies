# 🖥️ Operating System — Unit I: Complete Beginner-Friendly Notes

> **How to use these notes:** Read top to bottom. Every concept is explained with a simple analogy first, then the technical definition. Don't skip analogies — they are the key to truly *understanding* rather than just memorizing.

---

## 📌 Table of Contents

1. [What is an Operating System?](#1-what-is-an-operating-system)
2. [Functions of an OS](#2-functions-of-an-os)
3. [Types of Operating Systems](#3-types-of-operating-systems)
4. [Structure of an OS — Kernel & System Calls](#4-structure-of-an-os--kernel--system-calls)
5. [Process — The Heart of OS](#5-process--the-heart-of-os)
6. [CPU Scheduling Algorithms](#6-cpu-scheduling-algorithms)
7. [Process Synchronization & IPC](#7-process-synchronization--ipc)
8. [Deadlock](#8-deadlock)
9. [Memory Management](#9-memory-management)
10. [Virtual Memory & Page Replacement](#10-virtual-memory--page-replacement)
11. [Quick Revision Cheat Sheet](#11-quick-revision-cheat-sheet)

---

## 1. What is an Operating System?

### 🍳 The Kitchen Analogy

Imagine a **professional restaurant kitchen**:

```
👨‍🍳 CHEF (OS) manages everything:

  🥩 Ingredients = Hardware (CPU, RAM, Disk)
  🧑‍💼 Customers  = Users
  📋 Orders     = Programs/Applications
  👨‍🍳 Chef       = Operating System
```

- The chef doesn't serve the food himself — he **manages the kitchen**
- He decides which order gets cooked first (**CPU Scheduling**)
- He ensures two cooks don't grab the same knife at once (**Synchronization**)
- He tracks which ingredients are available (**Memory Management**)

> **Technical Definition:** An Operating System is system software that acts as an **interface between the user and the computer hardware**. It manages hardware resources and provides a platform to run application software.

### 📊 Layered View of a Computer System

```
┌─────────────────────────────────────────┐
│           👤 USER                        │
├─────────────────────────────────────────┤
│     📱 APPLICATION SOFTWARE              │
│   (Browser, Game, Word Processor)        │
├─────────────────────────────────────────┤
│   ⚙️  OPERATING SYSTEM  ← YOU ARE HERE   │
│   (Windows, Linux, macOS, Android)       │
├─────────────────────────────────────────┤
│   🔩 HARDWARE                            │
│   (CPU, RAM, Hard Disk, I/O Devices)     │
└─────────────────────────────────────────┘
```

The OS sits **between** the hardware and the applications. It hides the complexity of hardware from users and programmers.

---

## 2. Functions of an OS

Think of the OS as a **government** for your computer. Just like a government manages roads, police, hospitals, and money — the OS manages computer resources.

| OS Function | Real-World Analogy |
|---|---|
| **Process Management** | Traffic police managing vehicles on roads |
| **Memory Management** | Real estate agency allocating office spaces |
| **File System Management** | Library organizing books on shelves |
| **Device Management** | Hotel reception assigning rooms to guests |
| **Security & Protection** | Border security controlling entry/exit |
| **User Interface** | Receptionist helping you interact with the system |

### Core Objectives (3 E's)

```
1. 📌 EASE (Convenience)
   → Makes the computer easy to use
   → GUI, command line, etc.

2. ⚡ EFFICIENCY
   → Uses hardware resources optimally
   → No processor sitting idle, no memory wasted

3. 🔄 EVOLUTION
   → Allows new hardware/software updates
   → Old programs still work on new hardware
```

---

## 3. Types of Operating Systems

### 🏭 3.1 Batch Operating System

**Analogy:** Think of a **dhobi (laundry man)**. He doesn't wash each shirt as you give it. He waits, collects a *batch* of clothes, and washes them all together at once.

```
Jobs collected → Grouped by type → Executed together → Output

  [Payroll jobs] → [Run as batch] → [Output printed]
  [Report jobs]  → [Run as batch] → [Output printed]
```

- **No user interaction** during execution
- Jobs are collected, sorted, and run sequentially
- Early IBM computers used this (1950s–1970s)

| ✅ Advantages | ❌ Disadvantages |
|---|---|
| High CPU utilization | No interactive debugging |
| Good for repetitive jobs | Slow turnaround time |
| Simple to implement | One error can kill entire batch |

**Examples:** Payroll systems, Bank statement generation

---

### ⏱️ 3.2 Time-Sharing (Multitasking) OS

**Analogy:** A **single teacher** in a classroom with 30 students. She spends 2 minutes with each student, rotating around the class. Each student *feels* like they have the teacher's full attention.

```
CPU rotates between processes rapidly:

  Process A ──▶ [2ms] ──▶ Process B ──▶ [2ms] ──▶ Process C ──▶ ...
  
  So fast that each user thinks they have the whole CPU!
```

- Uses **time slices** (also called quanta)
- Multiple users interact simultaneously
- Response time is very short

| ✅ Advantages | ❌ Disadvantages |
|---|---|
| Multiple users simultaneously | Security between users is complex |
| Highly responsive | Context switching overhead |
| Resources fully utilized | Concurrency bugs can occur |

**Examples:** Linux, macOS, Windows, any modern desktop OS

---

### 🌐 3.3 Distributed OS

**Analogy:** Like a **team of doctors** in different cities connected by video call. They all share information and work together, but the patient just talks to one doctor — they don't see the complexity behind.

```
Computer A ──┐
Computer B ──┼──▶ [Network] ──▶ Appears as ONE system to the user
Computer C ──┘
```

- Collection of **independent computers** connected via network
- Appear as a **single unified system**
- Load is shared across machines

| ✅ Advantages | ❌ Disadvantages |
|---|---|
| High reliability (no single point of failure) | Complex to design |
| Resource sharing across machines | Network communication overhead |
| Scalable — add more machines | Security challenges |

**Examples:** LOCUS, Amoeba, Google's internal systems, cloud computing

---

### ⚡ 3.4 Real-Time OS (RTOS)

**Analogy:** A **911 emergency dispatch system**. When someone calls, the response MUST happen within a specific time. A 10-second delay could cost a life. The **deadline is everything**.

```
RTOS Types:

  🔴 HARD RTOS          🟡 SOFT RTOS
  │                     │
  │ Missing deadline =   │ Missing deadline =
  │ SYSTEM FAILURE       │ Degraded performance
  │                     │
  │ Pacemaker, Autopilot │ Video streaming, VoIP
```

- Guarantees tasks complete within **strict time limits**
- **Hard RTOS:** Deadline MUST be met (e.g., airbag deployment — a 10ms delay could fail to save lives)
- **Soft RTOS:** Deadline is desirable but not catastrophic if missed (e.g., video buffering)

**Examples:** VxWorks, FreeRTOS, QNX, RTEMS

---

### 📟 3.5 Embedded OS

**Analogy:** The **software inside your microwave**. It only knows one job — heat food. It doesn't run games or browse the internet. It's minimal, dedicated, and always on.

```
Embedded OS lives INSIDE a specific device:

  🚗 Car Engine Control  →  Dedicated OS
  🖨️ Printer              →  Dedicated OS
  📱 Smart Watch          →  Specialized OS
  🌡️ Digital Thermometer  →  Micro OS
```

- Built into the device's ROM
- Very **lightweight** (tiny memory footprint)
- Does **one specific task** very well

**Examples:** Embedded Linux, Android Things, RTOS variants

---

### 📊 All Types — Quick Comparison Table

| Feature | Batch | Time-Sharing | Distributed | RTOS | Embedded |
|---|---|---|---|---|---|
| User Interaction | ❌ None | ✅ High | ✅ Moderate | Limited | ❌ None |
| Response Time | Slow | Fast | Moderate | Ultra-fast | Fast |
| Multiple Users | ❌ | ✅ | ✅ | ❌ | ❌ |
| Cost | Low | Moderate | High | High | Low |
| Use Case | Bulk jobs | Daily computing | Cloud/Grid | Safety-critical | Appliances |

---

## 4. Structure of an OS — Kernel & System Calls

### 🧠 4.1 What is a Kernel?

**Analogy:** The kernel is the **Prime Minister** of a country. While the President (OS) is the face, the Prime Minister actually runs the day-to-day operations in a protected office that the public cannot enter.

```
┌───────────────────────────────────────┐
│           USER SPACE (Ring 3)          │
│   Your apps run here (browser, game)  │
│   ← LOW PRIVILEGE, RESTRICTED →       │
├───────────────────────────────────────┤  ← WALL (Protected boundary)
│           KERNEL SPACE (Ring 0)        │
│   OS Core runs here (Always in RAM)   │
│   ← FULL ACCESS TO HARDWARE →         │
└───────────────────────────────────────┘
```

The kernel is always resident in RAM from boot to shutdown.

---

### 🏗️ Types of Kernels

#### Monolithic Kernel — "The Giant Castle"

```
┌──────────────────────────────────┐
│         KERNEL SPACE             │
│  ┌─────┐ ┌──────┐ ┌───────────┐ │
│  │ CPU │ │Memory│ │   File    │ │
│  │Sched│ │ Mgmt │ │  System   │ │
│  └─────┘ └──────┘ └───────────┘ │
│  ┌──────────┐ ┌────────────────┐│
│  │  Device  │ │     IPC        ││
│  │  Drivers │ │                ││
│  └──────────┘ └────────────────┘│
│  Everything in ONE big program   │
└──────────────────────────────────┘
```

- All OS services run in kernel space together
- Very **fast** (direct function calls)
- But: If one driver crashes → **ENTIRE OS crashes** (Blue Screen of Death!)
- **Examples:** Linux, Unix, older Windows

#### Microkernel — "The Lean Government"

```
┌─────────────────────────────────────┐
│           USER SPACE                 │
│  [File Server] [Driver] [Network]   │  ← Run as regular processes!
└──────────────────────┬──────────────┘
                       │ (Message passing)
┌──────────────────────▼──────────────┐
│           KERNEL SPACE (Tiny!)       │
│   Only: Scheduling + IPC + Memory   │
└──────────────────────────────────────┘
```

- Only the **bare minimum** stays in kernel space
- Services run in user space — if a driver crashes, it just restarts (OS survives!)
- Slower because of message passing overhead
- **Examples:** MINIX, QNX, L4

#### Hybrid Kernel — "Best of Both Worlds"

- Performance-critical parts in kernel space (like Monolithic)
- But modular design (can load/unload drivers safely)
- **Examples:** Windows NT, macOS (XNU kernel)

| Kernel Type | Speed | Stability | Complexity | Examples |
|---|---|---|---|---|
| Monolithic | ⚡ Fast | 😰 Fragile | Medium | Linux, Unix |
| Microkernel | 🐢 Slower | 💪 Very Stable | High | MINIX, QNX |
| Hybrid | ⚡ Fast | 👍 Good | High | Windows, macOS |

---

### 📞 4.2 System Calls — Talking to the Kernel

**Analogy:** Imagine a **bank**. You (user application) cannot walk into the vault yourself. You fill out a **withdrawal form** (system call), hand it to the teller, and the teller (kernel) accesses the vault for you.

```
USER PROGRAM                     KERNEL
    │                                │
    │  "I want to read file.txt"     │
    │──── system call (read) ───────▶│
    │                                │── accesses disk hardware
    │                                │── reads data
    │◀─── returns file data ─────────│
    │                                │
    │ CPU switches mode:             │
    │  User Mode → Kernel Mode       │
    │  (then back after done)        │
```

#### System Call Execution Steps

```
Step 1: App calls library function    printf("Hello")
        │
Step 2: Library executes trap         INT 0x80  or  SYSCALL
        │
Step 3: CPU switches to Kernel Mode   Ring 3 → Ring 0
        │
Step 4: OS identifies & handles       "It's a write() call → send to screen"
        │
Step 5: CPU switches back             Ring 0 → Ring 3
        │
Step 6: Return to user program        printf returns
```

#### Categories of System Calls

| Category | What it does | Examples |
|---|---|---|
| **Process Control** | Create, kill, wait for processes | `fork()`, `exec()`, `exit()` |
| **File Management** | Open, read, write, close files | `open()`, `read()`, `write()` |
| **Device Management** | Request/release I/O devices | `ioctl()`, `read()`, `write()` |
| **Information Maintenance** | Get system info/time | `getpid()`, `time()` |
| **Communication** | IPC between processes | `pipe()`, `shmget()`, `socket()` |

---

## 5. Process — The Heart of OS

### 🎯 5.1 Process vs Program

**Analogy:**
- A **Program** is a **recipe written in a book** — it's static, just instructions on paper
- A **Process** is the **actual cooking happening** — the recipe in action, using ingredients (memory), a stove (CPU), and a cook's time

```
PROGRAM (passive)          PROCESS (active)
─────────────────          ─────────────────
Code on disk               Code LOADED in RAM
Stored in .exe file        Being EXECUTED by CPU
No resources allocated     HAS: memory, CPU time, file handles
```

### 📋 5.2 Process Control Block (PCB)

Every process is represented in the OS by a data structure called a **PCB** — think of it as a **patient's file** in a hospital:

```
┌──────────────────────────────┐
│       PROCESS CONTROL BLOCK  │
├──────────────────────────────┤
│ Process ID (PID)      : 1234 │  ← Unique identity
│ Process State         : Ready│  ← Current status
│ Program Counter       : 0x4A8│  ← Next instruction to execute
│ CPU Registers         : ...  │  ← Snapshot of CPU state
│ Memory Limits         : ...  │  ← Where in RAM it lives
│ Open Files List       : ...  │  ← Files it has open
│ Priority              : 5    │  ← Scheduling priority
│ Parent PID            : 1    │  ← Who created it
└──────────────────────────────┘
```

When a process is stopped (preempted), all its info is saved in the PCB. When it runs again, the CPU is restored to the exact state it was in before. This is called a **Context Switch**.

---

### 🔄 5.3 Process States & State Transition Diagram

**Analogy:** A student's life cycle in a class:

```
📝 NEW → Class begins, student REGISTERED
👋 READY → Student is present, waiting for teacher's attention  
🎓 RUNNING → Teacher is talking TO this student right now
😴 WAITING → Student raised hand, waiting for teacher (I/O wait)
🚪 TERMINATED → Student finished exam, LEFT the class
```

```
State Transition Diagram:

              Admitted
    ┌─────┐ ──────────▶ ┌───────┐ ─── Scheduler ──▶ ┌─────────┐
    │ NEW │             │ READY │    Dispatches       │ RUNNING │
    └─────┘             └───────┘                     └────┬────┘
                             ▲                             │
                             │  I/O Complete               │ I/O Request or
                             │  / Event Done               │ Event Wait
                        ┌────┴──────┐                      │
                        │  WAITING  │ ◀────────────────────┘
                        │ (Blocked) │
                        └───────────┘
                                           ┌────────────┐
    RUNNING ──── Interrupt (time up) ────▶ │   READY    │
    RUNNING ──── Exit / Error ──────────▶  │ TERMINATED │
                                           └────────────┘
```

| State | Meaning |
|---|---|
| **New** | Process just created, not yet in memory |
| **Ready** | In memory, waiting to be given CPU |
| **Running** | Currently executing on CPU |
| **Waiting/Blocked** | Waiting for I/O or an event (e.g., disk read) |
| **Terminated** | Finished execution, PCB being cleaned up |

---

### 🔀 5.4 Context Switching

**Analogy:** You're reading a book and your phone rings. You mark the page (save state), answer the phone (switch to new task), then come back and open to the marked page (restore state). That bookmark = PCB.

```
Process A running         Context Switch       Process B running
─────────────────         ─────────────        ─────────────────
[CPU executes A]          1. Save A's PCB      [CPU executes B]
                          2. Load B's PCB
                          ← Overhead time →
```

> ⚠️ Context switching has **overhead** — during the switch, no useful work is done. Too many switches = wasted CPU time.

---

## 6. CPU Scheduling Algorithms

### 📚 6.1 Why Scheduling is Needed

When multiple processes are in the Ready Queue, the OS must decide **who runs next**. This is the job of the **CPU Scheduler**.

**Key Terms (Must memorize!):**

```
AT  = Arrival Time   → When the process enters the ready queue
BT  = Burst Time     → How long it needs the CPU
CT  = Completion Time → When it finishes execution
TAT = TurnAround Time = CT - AT   (Total time from arrival to finish)
WT  = Waiting Time   = TAT - BT  (Time spent sitting in queue)
RT  = Response Time  = Time from arrival to FIRST CPU response
```

**Goal of a good scheduler:**
- ✅ Maximize CPU Utilization (keep CPU busy)
- ✅ Maximize Throughput (processes completed per unit time)
- ✅ Minimize TAT, WT, RT

---

### 🥇 6.2 FCFS — First Come First Served

**Analogy:** A **bank queue**. First person in line gets served first. Simple. Fair. But slow if the first person has 50 transactions.

**Type:** Non-preemptive (once a process gets CPU, it runs until done)

**Example:**

| Process | AT | BT |
|---|---|---|
| P1 | 0 | 6 |
| P2 | 1 | 4 |
| P3 | 2 | 2 |

```
Gantt Chart:
  0     6     10    12
  │ P1  │ P2  │ P3  │

  CT:  P1=6, P2=10, P3=12
  TAT: P1=6-0=6, P2=10-1=9, P3=12-2=10
  WT:  P1=0,     P2=5,       P3=8
  
  Avg WT = (0+5+8)/3 = 4.33
```

#### ⚠️ Convoy Effect (Big Problem with FCFS!)

```
Imagine: [Big Truck (P1, BT=100)] is ahead of [3 cars (P2,P3,P4, BT=2 each)]

  Cars wait 100 units for the truck to finish!
  
  This is the CONVOY EFFECT — short jobs stuck behind long ones.
```

---

### ✂️ 6.3 SJF — Shortest Job First

**Analogy:** A doctor's clinic where **patients with minor ailments** are seen first (they take less time), so the waiting room clears faster. But patients with serious (long) conditions wait forever if more minor patients keep arriving.

**Type:** Both non-preemptive (SJF) and preemptive (SRTF) versions exist

**Non-Preemptive SJF Example:**

| Process | AT | BT |
|---|---|---|
| P1 | 0 | 8 |
| P2 | 1 | 4 |
| P3 | 2 | 2 |
| P4 | 3 | 1 |

```
At t=0: Only P1 available → P1 runs
At t=8: P2(BT=4), P3(BT=2), P4(BT=1) all arrived → Shortest first

Gantt: 0──P1──8──P4──9──P3──11──P2──15

Avg WT = ((0) + (6) + (3) + (1)) / 4 = 2.5   ← Much better than FCFS!
```

**Preemptive SJF = SRTF (Shortest Remaining Time First):**
At every moment, if a new process arrives with shorter remaining time than current process, preempt!

#### ⚠️ Starvation Problem with SJF

```
Long process P1 (BT=100) arrives.
Short jobs keep arriving: P2(BT=2), P3(BT=1), P4(BT=3) ...

P1 NEVER gets to run! It starves.

SOLUTION → Aging: The longer a process waits, the higher its priority becomes.
           Eventually it gets high enough to run.
```

---

### 🎖️ 6.4 Priority Scheduling

**Analogy:** Like a **hospital emergency room**. A patient with a heart attack (high priority) is treated before someone with a minor cut (low priority), regardless of who arrived first.

**Type:** Can be preemptive or non-preemptive

```
  Higher number = Higher priority (convention varies)
  
  P1 (Priority 3) │────────────────────────│
  P2 (Priority 1) │──────────────────────────────────│  (LOW priority, waits)
  P3 (Priority 5) │──────│  (Highest, runs first)
  
  Order: P3 → P1 → P2
```

**⚠️ Starvation** — Same issue as SJF. Low-priority processes may never run.

**✅ Solution: Aging**
```
Every N minutes a process waits → increase its priority by 1

P2 starts at priority 1.
After 10 min waiting → priority becomes 2
After 20 min waiting → priority becomes 3
...Eventually it will become the highest priority and run.
```

---

### 🔄 6.5 Round Robin (RR)

**Analogy:** A **children's game of musical chairs** or **rotating turns**. Each child gets exactly 30 seconds to sit before the next child gets a turn. Fair, and everyone gets a chance quickly.

**Type:** Preemptive. Uses a **Time Quantum (Q)** — a fixed time slice.

```
Time Quantum (Q) = 2

Processes: P1(BT=6), P2(BT=4), P3(BT=2)

Ready Queue at t=0: [P1, P2, P3]

  0──P1(2)──2──P2(2)──4──P3(2)──6──P1(2)──8──P2(2)──10──P1(2)──12

Explanation:
  t=0 : P1 gets Q=2, runs until t=2 (remaining BT=4)
  t=2 : P2 gets Q=2, runs until t=4 (remaining BT=2)
  t=4 : P3 gets Q=2, runs until t=6 (DONE, BT=0)
  t=6 : P1 gets Q=2, runs until t=8 (remaining BT=2)
  t=8 : P2 gets Q=2, runs until t=10 (DONE)
  t=10: P1 gets Q=2, runs until t=12 (DONE)
```

#### ⚠️ Choosing the Right Time Quantum

```
Q too SMALL:
  │─P1─│─P2─│─P3─│─P1─│  ← Too many context switches
  Each switch wastes time → CPU spends more time switching than working!

Q too LARGE:
  │────────── P1 ──────────│─── P2 ───│  
  Behaves like FCFS → poor response time

IDEAL Q: Slightly larger than average burst time. Rule of thumb: 80% of
         processes should complete within one quantum.
```

---

### 📊 6.6 Algorithm Comparison Summary

| Algorithm | Type | Advantages | Disadvantages | Starvation? |
|---|---|---|---|---|
| FCFS | Non-preemptive | Simple | Convoy effect, high avg WT | No |
| SJF | Non-preemptive | Optimal avg WT | Requires knowing BT; starvation | Yes |
| SRTF | Preemptive | Best avg WT | High overhead; starvation | Yes |
| Priority | Both | Important jobs run first | Starvation of low-priority | Yes |
| Round Robin | Preemptive | Fair; good response time | High context-switch overhead | No |

---

## 7. Process Synchronization & IPC

### 🏁 7.1 The Race Condition Problem

**Analogy:** Two people checking the same bank account at the same moment:

```
Account Balance = ₹1000

Person A reads balance: 1000
Person B reads balance: 1000
Person A adds ₹500:     1000 + 500 = 1500 → writes 1500
Person B adds ₹200:     1000 + 200 = 1200 → writes 1200 ← WRONG!

Final balance = ₹1200 (should be ₹1700!)

This is a RACE CONDITION — the result depends on who writes last.
```

In code terms:
```c
// Two processes running this simultaneously:
counter = counter + 1;

// Internally, this is 3 operations:
//   1. LOAD counter into register
//   2. ADD 1 to register
//   3. STORE register back to counter

// If both processes interleave these steps: WRONG RESULT!
```

---

### 🚦 7.2 The Critical Section Problem

The **Critical Section** is the part of code that accesses shared data.

```
Process Structure:
┌────────────────────────────┐
│  ENTRY SECTION             │  ← Ask permission to enter
│  ──────────────────────    │
│  CRITICAL SECTION          │  ← Access shared data (ONE at a time!)
│  ──────────────────────    │
│  EXIT SECTION              │  ← Signal that you're done
│  ──────────────────────    │
│  REMAINDER SECTION         │  ← Rest of the code (not critical)
└────────────────────────────┘
```

Any solution MUST satisfy 3 conditions:

```
1. 🔒 MUTUAL EXCLUSION
   Only ONE process in the critical section at a time.
   (Like a single-person bathroom — one person inside, door locked)

2. 📈 PROGRESS
   If no one is in CS, a waiting process should be able to enter.
   (The bathroom shouldn't stay locked when it's empty)

3. ⏰ BOUNDED WAITING
   A process must get its turn within a bounded number of tries.
   (You can't wait forever outside the bathroom while others skip you)
```

---

### 🔐 7.3 Semaphores

**Analogy:** A **parking lot** with limited spaces. A semaphore is a counter of available spaces:

```
Parking Lot has 3 spaces (Semaphore S = 3):

Car arrives   → wait(S): S becomes 2, car parks
Car arrives   → wait(S): S becomes 1, car parks
Car arrives   → wait(S): S becomes 0, car parks
Car arrives   → wait(S): S becomes -1 → CAR BLOCKS (no space, wait!)

Car leaves    → signal(S): S becomes 0 → wake up waiting car!
```

**Operations:**
```c
wait(S):           // Also called P(S) or down(S)
  S = S - 1
  if S < 0:
    BLOCK this process (add to waiting queue)

signal(S):         // Also called V(S) or up(S)
  S = S + 1
  if S <= 0:
    WAKE UP one waiting process
```

#### Types of Semaphores:

```
COUNTING SEMAPHORE      BINARY SEMAPHORE (Mutex)
────────────────────    ────────────────────────
S can be any integer    S can only be 0 or 1
Used for resource       Used for mutual exclusion
counting                (like a lock)

e.g., 5 printers        e.g., one critical section
S = 5 initially         S = 1 (unlocked) or 0 (locked)
```

#### Classic Problems Using Semaphores:

**Producer-Consumer Problem:**
```
Producer fills a buffer; Consumer reads from buffer.
Problem: Producer must WAIT if buffer is FULL.
         Consumer must WAIT if buffer is EMPTY.

Solution:
  empty = N (N buffer slots empty)
  full  = 0 (0 slots filled)
  mutex = 1 (binary semaphore for buffer access)

Producer:               Consumer:
  wait(empty)             wait(full)
  wait(mutex)             wait(mutex)
  [add item]              [remove item]
  signal(mutex)           signal(mutex)
  signal(full)            signal(empty)
```

---

### 🔑 7.4 Mutex vs Semaphore

| Feature | Mutex | Binary Semaphore |
|---|---|---|
| **Value** | Locked/Unlocked | 0 or 1 |
| **Ownership** | ✅ Yes — only locker can unlock | ❌ Any process can signal |
| **Purpose** | Mutual exclusion only | Both mutual exclusion & signaling |
| **Analogy** | Personal key to your locker | Token/ticket system |

---

### 🤝 7.5 Inter-Process Communication (IPC)

Processes sometimes need to **communicate** (not just share resources). Two main methods:

#### Method 1: Shared Memory

```
Process A ──┐
            ├──▶ [Shared Memory Region] ◀──┬── Process B
            │                              │
Process A writes → Process B reads directly from same memory
```

- **Fast** — no system calls needed during data transfer
- **Problem** — processes must synchronize access themselves

#### Method 2: Message Passing

```
Process A ────── send(message) ────▶ [OS Mailbox / Channel] ────▶ Process B
Process B ────── receive(message) ◀─────────────────────────────
```

- No shared memory needed — useful for processes on **different computers**
- **Slower** — every message involves system calls
- **Safer** — OS manages the channel

---

## 8. Deadlock

### 💀 8.1 What is Deadlock?

**Analogy — The Bridge Problem:**
```
🚗 Car A is coming from the left, carrying a PLANK.
🚗 Car B is coming from the right, carrying a PLANK.
Both meet in the middle of a narrow bridge.

Car A says: "I'll move when B moves."
Car B says: "I'll move when A moves."

DEADLOCK — Neither can move. Forever stuck!
```

**Technical definition:** A set of processes are **deadlocked** when each process is holding a resource and waiting for a resource held by another process in the set.

```
Resource Allocation Graph (showing deadlock):

P1 ──holds──▶ R1 ◀──wants── P2
│                             │
└──wants──▶ R2 ──holds───────┘

P1 holds R1, wants R2
P2 holds R2, wants R1
→ CIRCULAR WAIT → DEADLOCK
```

---

### 🔍 8.2 The 4 Coffman Conditions

ALL FOUR must be present simultaneously for deadlock to occur. Remove even ONE → no deadlock possible.

```
1. 🔒 MUTUAL EXCLUSION
   At least one resource is non-shareable.
   (Only one process can use it at a time)
   Example: A printer can't print two jobs at once.

2. ✋ HOLD AND WAIT
   A process holds ≥1 resource while waiting for more.
   Example: P1 holds the scanner, waiting for the printer.

3. 🚫 NO PREEMPTION
   Resources can't be forcibly taken from a process.
   Example: OS can't snatch the scanner from P1 by force.

4. 🔁 CIRCULAR WAIT
   A chain of processes: P1→P2→P3→...→P1
   Each waiting for the next one's resource.
```

---

### 🛡️ 8.3 Deadlock Handling Strategies

#### Strategy 1: Prevention (Break a Coffman Condition)

```
Break HOLD AND WAIT:
  → Require processes to request ALL resources at the start.
  → If can't get all, release everything and try again.
  Downside: Low resource utilization; starvation possible.

Break CIRCULAR WAIT:
  → Assign a global order to resources (R1, R2, R3...)
  → Processes must always request in increasing order.
  → Circular wait becomes impossible!
  Example: Always request File before Printer, never the reverse.
```

#### Strategy 2: Avoidance (Banker's Algorithm)

**Analogy:** A **bank manager** who only gives loans if the bank can still survive even if the worst happens (all borrowers default at once).

```
Key concept: SAFE STATE vs UNSAFE STATE

SAFE STATE:  There exists a sequence where every process can finish.
UNSAFE STATE: No such sequence exists → deadlock MIGHT occur.

OS says "YES" to resource requests ONLY if the result is a SAFE STATE.
```

**Banker's Algorithm (for multiple resource types):**

Given:
- **Allocation** matrix — what each process currently holds
- **Max** matrix — what each process may need at most
- **Available** vector — resources currently free

```
Need = Max - Allocation

Algorithm:
1. Find a process whose Need ≤ Available
2. "Give" it the resources (simulate), let it finish, it releases everything
3. Add released resources to Available
4. Repeat until all processes finish → SAFE STATE ✅
   If no such process found at any step → UNSAFE STATE ❌
```

#### Strategy 3: Detection & Recovery

Let deadlock happen, then deal with it:

```
Detection:
  Run Resource Allocation Graph reduction algorithm periodically.
  If cycles remain → Deadlock detected!

Recovery Options:
  Option A: Abort ALL deadlocked processes (expensive, work lost)
  Option B: Abort ONE at a time until cycle broken (careful selection)
  Option C: Preempt resources (take from one, give to another)
```

#### Strategy 4: Ostrich Algorithm (Ignore!)

```
"If you ignore a problem long enough, maybe it goes away."
                              — Ostrich burying its head in sand

Windows and Linux use this approach!

Why? Deadlocks are rare in practice.
     Handling them has complexity overhead.
     Easier to just REBOOT if one occurs.
```

---

## 9. Memory Management

### 🏠 9.1 Why Memory Management?

**Analogy:** An **apartment complex** with 1000 rooms (RAM). The building manager (OS) must:
- Assign rooms to tenants (processes)
- Keep track of empty rooms
- Handle when tenants move out

**Goals:**
- **Relocation** — A process can be loaded anywhere in RAM
- **Protection** — Processes cannot access each other's memory
- **Sharing** — Allow controlled sharing (e.g., shared library code)
- **Efficiency** — Minimize wasted space

---

### 🗺️ 9.2 Logical vs Physical Address

```
LOGICAL ADDRESS (Virtual Address)         PHYSICAL ADDRESS (Real Address)
─────────────────────────────────         ────────────────────────────────
Generated by CPU during execution         Actual location in RAM
Starts from 0 for every process           Unique, real hardware address
"Page 3, Offset 50" (what CPU sees)       "RAM location 8254" (what RAM sees)

CPU → [MMU (Memory Management Unit)] → RAM
      (Translates logical to physical)
```

---

### 📄 9.3 Paging

**Analogy:** You have 100 book pages to store. You have 10 binders, each holding 10 pages. You don't need to keep pages in order — page 1 can be in binder 5, page 2 in binder 1, etc. You keep an **index** (page table) noting where each page is.

```
Physical Memory (RAM):           Logical Memory (Process View):
Divided into FRAMES              Divided into PAGES

Frame 0 │ [OS data]     │         Page 0 │ [Code]  │
Frame 1 │ [P1 Page 0]   │◀──┐     Page 1 │ [Data]  │
Frame 2 │ [P2 Page 0]   │   │     Page 2 │ [Stack] │
Frame 3 │ [P1 Page 1]   │◀──┼─── Page Table ───┤
Frame 4 │ [empty]       │   │                   │
Frame 5 │ [P1 Page 2]   │◀──┘
```

**Address Translation:**

```
Logical Address = [Page Number (p)] [Page Offset (d)]
                        │                  │
                        ▼                  │
                   Page Table              │
                   maps p → f             │
                        │                  │
Physical Address = [Frame Number (f)] [Offset (d)]
```

**Example:**
```
Page size = 4KB = 2^12 bytes → offset uses 12 bits
Total logical address = 32 bits
Page number = 32 - 12 = 20 bits → 2^20 = 1M pages

Logical address: 0x00003A5B
  Page number = 0x00003 = 3
  Offset      = 0xA5B = 2651

Page table says: Page 3 → Frame 7
Physical address: Frame 7 → 0x00007A5B
```

#### TLB — Translation Lookaside Buffer

**Analogy:** Instead of looking up a dictionary (Page Table in RAM) every single time you need a word, you keep a **sticky note with the 10 most common words** on your desk. That's the TLB.

```
Without TLB: Every memory access = 2 RAM accesses (PT lookup + actual data)
With TLB:    Most accesses = 1.x RAM accesses (TLB hit ≈ instant)

TLB Hit:  page p in TLB? YES → use frame directly → fast!
TLB Miss: page p not in TLB → check page table (slow) → update TLB
```

#### Fragmentation in Paging:

```
INTERNAL FRAGMENTATION (in paging):
  Page size = 4KB
  Process needs 9KB → gets 3 pages (12KB)
  Waste = 12 - 9 = 3KB (inside the last page, wasted)
  
  [Page 0: 4KB used] [Page 1: 4KB used] [Page 2: 1KB used + 3KB WASTED]

EXTERNAL FRAGMENTATION (NOT in paging):
  Paging ELIMINATES external fragmentation because ANY free frame can be used!
```

---

### 📦 9.4 Segmentation

**Analogy:** Instead of dividing a book into fixed-size chapters (paging), segmentation divides it **logically** — Chapter 1 might be 20 pages, Chapter 2 might be 5 pages, etc.

```
Process is divided into LOGICAL SEGMENTS:

Segment 0: CODE   (e.g., 1500 bytes)
Segment 1: DATA   (e.g., 3000 bytes)
Segment 2: STACK  (e.g., 500 bytes)

Each segment is a contiguous chunk in RAM, but segments
can be anywhere in RAM.

Segment Table: [Segment #] → [Base address in RAM, Limit/Length]
```

**Address Translation:**
```
Logical Address = [Segment # (s)] [Offset (d)]
                       │               │
                  Segment Table        │
                  Base[s] + d = Physical address
                  
Check: d < Limit[s] ? Valid : Segmentation Fault!
```

#### Fragmentation in Segmentation:

```
EXTERNAL FRAGMENTATION (YES, segmentation has this!):
  Segments of variable sizes leave holes in memory.
  
  [OS] [Seg A: 3KB] [free: 2KB] [Seg B: 5KB] [free: 1KB] [Seg C: 4KB]
  
  Total free = 3KB, but no contiguous 3KB block!
  A new process needing 3KB can't be loaded!

INTERNAL FRAGMENTATION (NOT in segmentation):
  Segments are exactly as big as needed.
```

---

### 🔑 9.5 Paging vs Segmentation

| Feature | Paging | Segmentation |
|---|---|---|
| Division Unit | Fixed-size pages | Variable-size segments |
| User Visibility | Invisible to programmer | Visible (code, data, stack) |
| External Fragmentation | ❌ None | ✅ Yes |
| Internal Fragmentation | ✅ Yes (last page) | ❌ None |
| Address | Page # + Offset | Segment # + Offset |

---

## 10. Virtual Memory & Page Replacement

### 🌌 10.1 What is Virtual Memory?

**Analogy:** Your desk is small (RAM). You're working on a huge project with thousands of papers. You can't fit all papers on your desk. So, most papers are in a filing cabinet (disk). You keep only what you're currently working on on your desk. When you need something from the cabinet, you fetch it. When your desk is full, you put something back.

```
Virtual Memory says:
  "Process can be LARGER than physical RAM!"
  
  Full Process = 100MB
  RAM available = 20MB
  
  OS loads only what's needed RIGHT NOW into RAM.
  Rest stays on disk (swap space).
```

**Benefits:**
- Programs can be larger than RAM
- More processes can run simultaneously (each partially in RAM)
- Memory can be shared between processes

---

### 📄 10.2 Demand Paging

Only load a page into RAM **when it is demanded** (accessed by CPU).

```
Process starts → Only ENTRY POINT page loaded
                    ↓
CPU accesses page → Page in RAM? Run normally
                 → Page NOT in RAM? → PAGE FAULT
```

**Page Fault Flow:**

```
CPU accesses address
        │
        ▼
Is page in RAM? (Check valid bit in page table)
   │         │
  YES        NO ← PAGE FAULT
   │          │
   ▼          ▼
Access it!  OS takes over:
            1. Find page location on disk
            2. Is there a free frame in RAM?
               → YES: Load page there
               → NO: Choose a VICTIM page to evict (Page Replacement!)
            3. Update page table (set valid bit)
            4. Restart the CPU instruction that caused the fault
```

**Performance:**
```
Effective Access Time (EAT) = (1-p) × memory access time + p × page fault time

Where p = page fault rate (very small in practice, e.g., 0.001)

Page fault time is HUGE (disk access ≈ 10ms vs RAM ≈ 100ns)
So even 1 fault per 1000 accesses can slow down by 40x!
```

---

### 🔄 10.3 Page Replacement Algorithms

When RAM is full and a new page is needed, which existing page do we **evict** (swap to disk)?

#### 🥇 FIFO — First In, First Out

**Analogy:** Grocery store shelf — oldest items at the front, newest at the back. When space needed, remove the front (oldest) item.

```
Reference String: 1, 2, 3, 4, 1, 2, 5, 1, 2, 3
Frames = 3

Initial: Empty, empty, empty

Ref 1: [1, -, -]  PAGE FAULT
Ref 2: [1, 2, -]  PAGE FAULT
Ref 3: [1, 2, 3]  PAGE FAULT
Ref 4: [4, 2, 3]  PAGE FAULT (evict 1, oldest)
Ref 1: [4, 1, 3]  PAGE FAULT (evict 2)
Ref 2: [4, 1, 2]  PAGE FAULT (evict 3)
Ref 5: [5, 1, 2]  PAGE FAULT (evict 4)
Ref 1: [5, 1, 2]  ✅ HIT
Ref 2: [5, 1, 2]  ✅ HIT
Ref 3: [5, 3, 2]  PAGE FAULT (evict 1)

Total faults = 8
```

**⚠️ Belady's Anomaly:**
```
Weird but true: Sometimes adding MORE frames causes MORE page faults with FIFO!

3 frames: 9 faults
4 frames: 10 faults  ← MORE faults with more memory! That's Belady's Anomaly.

LRU and OPT don't suffer from this problem.
```

---

#### 🕰️ LRU — Least Recently Used

**Analogy:** When your refrigerator is full, throw out the food you haven't touched in the longest time. (It's probably expired anyway!)

```
Replace the page that was LAST USED the LONGEST time AGO.

Reference String: 1, 2, 3, 4, 1, 2, 5, 1, 2, 3
Frames = 3

Ref 1: [1, -, -]  FAULT  (recently used: 1)
Ref 2: [1, 2, -]  FAULT  (recently used: 2, 1)
Ref 3: [1, 2, 3]  FAULT  (recently used: 3, 2, 1)
Ref 4: [4, 2, 3]  FAULT  (LRU=1, evict 1; recently used: 4, 3, 2)
Ref 1: [4, 1, 3]  FAULT  (LRU=2, evict 2)
Ref 2: [4, 1, 2]  FAULT  (LRU=3, evict 3)
Ref 5: [5, 1, 2]  FAULT  (LRU=4, evict 4)
Ref 1: [5, 1, 2]  ✅ HIT
Ref 2: [5, 1, 2]  ✅ HIT
Ref 3: [5, 3, 2]  FAULT  (LRU=1, evict 1)

Total faults = 8  (same here, but generally LRU is better)
```

**Implementation:** Hardware counter per page (stamp last use time) or Stack-based.

---

#### 🔮 Optimal (OPT) — Bélády's Algorithm

**Analogy:** A fortune teller who knows the future — evict the page that won't be needed for the longest time in the future.

```
Replace the page that will NOT be used for the LONGEST time in the future.

This is the BEST possible algorithm — minimum page faults.
But IMPOSSIBLE to implement in practice (requires future knowledge).

Used only as a BENCHMARK to compare other algorithms.
```

---

#### 📊 Page Replacement Comparison

| Algorithm | Faults | Belady's Anomaly | Implementable? |
|---|---|---|---|
| FIFO | High | Yes ❌ | Yes |
| LRU | Good | No ✅ | Yes (hardware support) |
| Optimal | Lowest | No ✅ | No (needs future) |

---

### 🌊 10.4 Thrashing

**Analogy:** A student trying to study for 10 subjects with only 2 hours sleep. They switch between subjects so fast they never actually learn anything. All time is spent switching, no actual studying.

```
Too many processes → Each gets very few frames → Constant page faults
→ Processes spend more time waiting for pages than computing
→ CPU utilization DROPS even as load increases!

      CPU
   Utilization
   │
100%│      ✨ optimal
   │    ╱    ╲
   │   ╱      ╲
 50%│  ╱        ╲
   │ ╱          ╲
   │╱            ╲______ THRASHING
   └─────────────────────
                  Degree of Multiprogramming
```

**Solutions:**
- **Working Set Model** — Identify the set of pages a process is actively using (its *working set*) and ensure they're all in RAM
- **Page Fault Frequency** — If fault rate is too high, give process more frames; if too low, take frames away

---

## 11. Quick Revision Cheat Sheet

### 🧠 Key Formulas

```
TAT = CT - AT          (TurnAround Time)
WT  = TAT - BT         (Waiting Time)
RT  = First CPU time - AT  (Response Time)
CPU Utilization = Busy time / Total time × 100%
Throughput = Processes completed / Total time
```

### 🔐 Coffman Conditions (All 4 → Deadlock)

```
M - Mutual Exclusion
H - Hold and Wait
N - No Preemption
C - Circular Wait
Memory tip: "My House, No Clutter"
```

### 📄 Fragmentation Types

```
INTERNAL: Wasted space INSIDE allocated block (Paging suffers)
EXTERNAL: Wasted space OUTSIDE in tiny gaps (Segmentation suffers)
```

### 🔄 Scheduling Algorithm Selection Guide

```
Simple batch jobs?          → FCFS
Minimize average WT?        → SJF / SRTF
Important jobs first?       → Priority (with Aging to prevent starvation)
Interactive/Fair system?    → Round Robin
Most real systems use?      → Multilevel feedback queue (combo of all)
```

### 🏷️ Key Definitions at a Glance

| Term | One-Line Definition |
|---|---|
| **OS** | Software managing hardware and providing services to applications |
| **Kernel** | Core of OS, always in RAM, runs in privileged mode |
| **System Call** | Interface to request OS services from user mode |
| **Process** | A program in execution (active, has resources) |
| **PCB** | Data structure holding all process information |
| **Semaphore** | Integer variable for process synchronization |
| **Deadlock** | Circular wait causing all involved processes to block forever |
| **Paging** | Fixed-size memory allocation; eliminates external fragmentation |
| **Segmentation** | Variable-size logical memory allocation |
| **Virtual Memory** | Illusion of more RAM using disk as extension |
| **Page Fault** | Accessing a page not currently in RAM |
| **TLB** | Cache for page table entries; speeds up address translation |
| **Thrashing** | Excessive paging causing near-zero CPU utilization |
| **LRU** | Replace the least recently used page during page replacement |

---

## 📝 Practice Questions

1. Explain the difference between a process and a program with an example.
2. Draw and explain the process state diagram with all transitions.
3. Given processes P1(AT=0,BT=8), P2(AT=1,BT=4), P3(AT=2,BT=2), P4(AT=3,BT=1) — calculate Gantt chart, TAT, WT for FCFS, SJF, and RR (Q=2).
4. Explain the four Coffman conditions with a real-world example.
5. Prove why Banker's Algorithm only approves requests that keep the system in a safe state.
6. Compare paging and segmentation — when would you prefer each?
7. Given a reference string [1,2,3,4,1,2,5,1,2,3,4,5] with 3 frames, calculate page faults using FIFO and LRU.
8. What is Belady's Anomaly? Which algorithms are immune to it?
9. Explain thrashing and how the Working Set Model prevents it.
10. What is the difference between a Binary Semaphore and a Mutex?

---

*📌 These notes cover the complete Unit I of Operating Systems. Happy studying! 🎓*