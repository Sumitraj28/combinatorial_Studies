# Unit I: Operating Systems - MCQ Bank

Practice these 50 high-yield, solved Multiple Choice Questions to master Unit 1 concepts. Every question includes the correct answer and a detailed explanation.

---

## 🔷 Topic 1: OS Foundations, Kernel & System Calls

#### Q1. The core component of an Operating System that runs in the most privileged mode (Ring 0) and remains in RAM throughout the session is:
- A) Shell
- B) Kernel
- C) Command Interpreter
- D) BIOS
- **Answer: ✅ B**
- **Explanation**: The kernel is the central core of the OS. The shell is a user-level program that interfaces with the kernel.

#### Q2. Which of the following is true regarding a Microkernel architecture?
- A) All services run in the kernel space for speed
- B) It is faster than a monolithic kernel because it has less code
- C) It keeps only essential services in kernel space; other services run as user processes
- D) A crash in a system driver crashes the entire system
- **Answer: ✅ C**
- **Explanation**: Microkernels keep only bare essentials (IPC, low-level scheduling) in kernel space, isolating drivers and files in user space to make the system more secure and robust, though at the expense of performance.

#### Q3. In Unix-like systems, the `fork()` system call returns:
- A) 0 to the parent process, and child's PID to the child process
- B) 0 to the child process, and child's PID to the parent process
- C) -1 to the child process on success
- D) PID of the parent to the child process
- **Answer: ✅ B**
- **Explanation**: On success, `fork()` creates a clone process. It returns `0` to the child and the child's process ID (PID) to the parent. It returns `-1` if creation fails.

#### Q4. Which instruction execution requires switching from User Mode to Kernel Mode?
- A) Calling a local mathematical function
- B) Modifying a local variable on the stack
- C) Reading a data block from the solid-state drive (SSD)
- D) Adding two values stored in CPU registers
- **Answer: ✅ C**
- **Explanation**: Accessing hardware like storage (I/O) is a privileged operation. The application must invoke a system call, which shifts the CPU execution mode from User to Kernel.

#### Q5. A computer program is a __________ entity, whereas a process is a __________ entity.
- A) Dynamic, Static
- B) Active, Passive
- C) Passive, Active
- D) Temporary, Permanent
- **Answer: ✅ C**
- **Explanation**: A program is a passive set of instructions stored on disk (code). A process is an active entity in execution, with resources like a program counter (PC), stack, registers, and memory.

---

## 🔷 Topic 2: Process States & CPU Scheduling

#### Q6. Which state transition is IMPOSSIBLE in a standard process state model?
- A) Ready $\to$ Running
- B) Running $\to$ Ready
- C) Waiting $\to$ Running
- D) Running $\to$ Waiting
- **Answer: ✅ C**
- **Explanation**: A process waiting for an I/O event must go back to the *Ready* queue once the event completes. It cannot jump straight to *Running* because it must wait for the CPU scheduler to select it.

#### Q7. The CPU scheduler dispatcher is responsible for:
- A) Moving a process from the New state to the Ready state
- B) Assigning a selected ready process to the CPU
- C) Allocating I/O devices to processes
- D) Calculating the time quantum for Round Robin
- **Answer: ✅ B**
- **Explanation**: The dispatcher is the module that gives control of the CPU to the process selected by the short-term scheduler.

#### Q8. Which CPU scheduling algorithm yields the minimum average waiting time for a set of stationary processes?
- A) First-Come, First-Served (FCFS)
- B) Round Robin (RR)
- C) Shortest Job First (SJF)
- D) Multilevel Queue Scheduling
- **Answer: ✅ C**
- **Explanation**: Shortest Job First (SJF) is mathematically proven to be optimal because it minimizes the average waiting time for any given set of processes.

#### Q9. Consider the following processes with their Arrival Time and Burst Time:
| Process | Arrival Time | Burst Time |
| :--- | :--- | :--- |
| P1 | 0 ms | 8 ms |
| P2 | 1 ms | 4 ms |
| P3 | 2 ms | 9 ms |

Using Non-Preemptive SJF, what is the completion time of P2?
- A) 12 ms
- B) 4 ms
- C) 13 ms
- D) 5 ms
- **Answer: ✅ A**
- **Explanation**: 
  - At $t=0$, only P1 is available. It runs to completion ($t=8$).
  - At $t=8$, both P2 and P3 have arrived. Since P2 has a shorter burst ($4 < 9$), P2 runs next.
  - P2 finishes at $8 + 4 = 12$ ms.

#### Q10. In Round Robin scheduling, if the Time Quantum is chosen to be extremely large (e.g., larger than the longest burst time):
- A) The scheduling degrades into FCFS
- B) The scheduling degrades into Shortest Job First
- C) Context switching overhead increases to 100%
- D) Starvation becomes high
- **Answer: ✅ A**
- **Explanation**: If the quantum is large enough, every process runs to completion in its first time slice without being preempted. Hence, it behaves exactly like First-Come, First-Served.

#### Q11. "Aging" is a synchronization or scheduling technique used to prevent:
- A) Deadlocks
- B) Race conditions
- C) Starvation
- D) Belady's Anomaly
- **Answer: ✅ C**
- **Explanation**: Aging gradually increases the priority of processes that have waited in the system for a long time, ensuring they eventually get CPU time and avoiding starvation.

#### Q12. Context switching is:
- A) Time spent performing user computations
- B) Pure overhead to save and restore process states
- C) A method to speed up memory access
- D) An algorithm to prevent page faults
- **Answer: ✅ B**
- **Explanation**: During a context switch, the OS performs no useful calculations for the user; it only saves the state of the old process and loads the state of the new one. Thus, it is pure overhead.

#### Q13. Which of the following is shared between threads belonging to the same process?
- A) Stack and registers
- B) Program counter and thread ID
- C) Global variables and open files
- D) Local variables and stack pointers
- **Answer: ✅ C**
- **Explanation**: Threads share the process's code, global data (data section), heap, and file descriptors. They maintain private stacks, registers, and program counters.

---

## 🔷 Topic 3: Process Synchronization

#### Q14. A race condition is:
- A) A situation where multiple processes compete for CPU scheduling time
- B) A scenario where several threads access shared data concurrently and the outcome depends on the execution order
- C) A physical hardware fault in the system clock
- D) An optimization technique in multi-core chips
- **Answer: ✅ B**
- **Explanation**: A race condition occurs when concurrent operations read and write shared state, making the final result highly dependent on execution scheduling.

#### Q15. Which of the following is NOT a necessary requirement to solve the Critical Section problem?
- A) Mutual Exclusion
- B) Progress
- C) Bounded Waiting
- D) Preemption
- **Answer: ✅ D**
- **Explanation**: The three requirements are Mutual Exclusion, Progress, and Bounded Waiting. Preemption is a design flag, not a correctness condition.

#### Q16. In Peterson's solution for two-process synchronization, process entry is controlled using:
- A) A single counting semaphore
- B) Hardware test-and-set instructions
- C) A flag array and a turn variable
- D) A binary mutex lock
- **Answer: ✅ C**
- **Explanation**: Peterson's is a software-based solution using `bool flag[2]` to show intent and `int turn` to yield priority.

#### Q17. The wait() operation on a semaphore S acts to:
- A) Increment the semaphore value and block if negative
- B) Decrement the semaphore value and block the process if S < 0
- C) Wake up a waiting process from the queue
- D) Release a Mutex lock
- **Answer: ✅ B**
- **Explanation**: `wait(S)` (or $P(S)$) decrements the semaphore value. If the value becomes negative, the executing process is added to the block queue.

#### Q18. What is the fundamental difference between a Mutex and a Binary Semaphore?
- A) A binary semaphore can take values up to $N$
- B) A Mutex has an ownership property: only the thread that locks it can unlock it
- C) Mutexes do not support mutual exclusion
- D) A binary semaphore is faster than a Mutex in user mode
- **Answer: ✅ B**
- **Explanation**: A mutex has ownership. A binary semaphore does not; one thread can wait on the semaphore, and a completely different thread can signal it.

---

## 🔷 Topic 4: Deadlocks

#### Q19. Which of the following is NOT one of the 4 necessary Coffman conditions for a deadlock?
- A) Hold and Wait
- B) Mutual Exclusion
- C) Circular Wait
- D) Resource Preemption
- **Answer: ✅ D**
- **Explanation**: The condition is **No Preemption** (resources cannot be forcibly taken). Preemption would actually *prevent* deadlocks.

#### Q20. If a Resource Allocation Graph (RAG) contains a cycle and resources have only a single instance:
- A) Deadlock might exist
- B) Deadlock definitely exists
- C) The system is in a safe state
- D) The cycle will resolve automatically
- **Answer: ✅ B**
- **Explanation**: In a single-instance RAG, a cycle is a necessary *and* sufficient condition for deadlock. If multiple instances exist, a cycle only indicates *possible* deadlock.

#### Q21. The Banker's Algorithm is used by an operating system to achieve:
- A) Deadlock Prevention
- B) Deadlock Avoidance
- C) Deadlock Detection
- D) Deadlock Recovery
- **Answer: ✅ B**
- **Explanation**: Banker's algorithm is an avoidance technique. It dynamically checks if allocating resources keeps the system in a "safe state".

#### Q22. To prevent deadlocks, breaking the "Hold and Wait" condition can be achieved by:
- A) Sharing all resources among all processes
- B) Forcing a process to request all its resources at once before execution
- C) Allowing resources to be preempted
- D) Restructuring resources in a strict hierarchy
- **Answer: ✅ B**
- **Explanation**: If a process must allocate all resources at once, it never holds some while waiting for others, thereby breaking Hold and Wait.

---

## 🔷 Topic 5: Memory Management

#### Q23. Paging solves the problem of:
- A) Internal Fragmentation
- B) External Fragmentation
- C) Virtual memory thrashing
- D) CPU starvation
- **Answer: ✅ B**
- **Explanation**: Since paging maps logical pages to non-contiguous physical frames, it eliminates external fragmentation. However, it can suffer from internal fragmentation in the last page.

#### Q24. In a paging system, the CPU generates a logical address containing:
- A) Page number and Page offset
- B) Frame number and Frame offset
- C) Segment table limit and Segment base
- D) Cache block and Tag
- **Answer: ✅ A**
- **Explanation**: The CPU-generated address has a page number ($p$) and page offset ($d$). The page table maps $p$ to a frame number $f$, while the offset $d$ remains unchanged.

#### Q25. What is the purpose of the Translation Lookaside Buffer (TLB)?
- A) To store temporary files during system boot
- B) To act as a fast hardware cache for page table lookups
- C) To replace secondary storage during page faults
- D) To schedule threads
- **Answer: ✅ B**
- **Explanation**: The TLB stores recently accessed page-to-frame translations in hardware, bypassing slow double memory references to the page table in RAM.

#### Q26. Let memory access time be $100\text{ ns}$ and TLB access time be $10\text{ ns}$. If the TLB hit ratio is $90\%$, what is the effective memory access time (EAT)?
- A) $110\text{ ns}$
- B) $120\text{ ns}$
- C) $100\text{ ns}$
- D) $130\text{ ns}$
- **Answer: ✅ B**
- **Explanation**: 
  - $\text{EAT} = h \times (t + m) + (1-h) \times (t + 2m)$
  - $\text{EAT} = 0.90 \times (10 + 100) + 0.10 \times (10 + 200)$
  - $\text{EAT} = 0.90 \times 110 + 0.10 \times 210 = 99 + 21 = 120\text{ ns}$.

#### Q27. Which page replacement algorithm can display Belady's Anomaly?
- A) Least Recently Used (LRU)
- B) First-In, First-Out (FIFO)
- C) Optimal (OPT)
- D) Least Frequently Used (LFU)
- **Answer: ✅ B**
- **Explanation**: Belady's Anomaly (where increasing the physical frame count increases page faults) can occur in FIFO. LRU and OPT do not exhibit this anomaly because they are stack algorithms.

#### Q28. A page fault occurs when:
- A) The page table gets corrupted
- B) The CPU references a page that is not currently loaded in main memory
- C) The program references an out-of-bounds pointer
- D) The TLB cache is full
- **Answer: ✅ B**
- **Explanation**: When a process references a page whose valid/invalid bit in the page table is set to "invalid" (meaning it's not in RAM), a page fault interrupt occurs, triggering the OS to fetch the page from disk.

#### Q29. Thrashing occurs in an operating system when:
- A) The CPU executes instructions too quickly for the system bus
- B) The system spends more time swapping pages in and out of disk than executing processes
- C) A process goes into an infinite loop
- D) Multiple disks in a RAID array crash simultaneously
- **Answer: ✅ B**
- **Explanation**: Thrashing happens when a process doesn't have enough frames allocated to support its active pages, leading to a constant cycle of page faults and page swapping.

#### Q30. Segmentation is a memory management scheme that:
- A) Divides memory into equal-sized pages
- B) Divides memory into variable-sized, logically meaningful segments
- C) Only works on secondary storage
- D) Prevents external fragmentation
- **Answer: ✅ B**
- **Explanation**: Segmentation divides memory into variable-sized blocks corresponding to logical units (like functions, stack, variables). It suffers from external fragmentation.

---

## 🔷 Topic 6: Storage, File Systems & Linux Commands

#### Q31. Which RAID level uses disk mirroring to write identical copies of data to separate drives, achieving 50% storage efficiency?
- A) RAID 0
- B) RAID 1
- C) RAID 5
- D) RAID 6
- **Answer: ✅ B**
- **Explanation**: RAID 1 (mirroring) clones data to two disks. It offers excellent fault tolerance but has a storage overhead of 50%.

#### Q32. In disk scheduling, the Shortest Seek Time First (SSTF) algorithm:
- A) Services requests in the order of their arrival
- B) Services requests closest to the current cylinder position of the disk head
- C) Moves the head from end to end like an elevator
- D) Suffers from no starvation
- **Answer: ✅ B**
- **Explanation**: SSTF selects the request that requires the least movement of the disk arm. It can cause starvation for far-away requests if closer ones keep arriving.

#### Q33. Which disk scheduling algorithm is also known as the "elevator" algorithm?
- A) FCFS
- B) SSTF
- C) SCAN
- D) C-LOOK
- **Answer: ✅ C**
- **Explanation**: SCAN moves the disk head in one direction servicing requests until it hits the end, then reverses direction, acting like an elevator.

#### Q34. An "Inode" in Unix-like file systems:
- A) Stores the actual file content blocks
- B) Is a directory containing user permissions
- C) Contains file metadata and pointers to data blocks
- D) Holds the system boot sector
- **Answer: ✅ C**
- **Explanation**: An inode (index node) contains properties (file size, permissions, owner, timestamps) and direct/indirect block pointers to the file's data blocks.

#### Q35. What does the Linux command `chmod 754 file.txt` do?
- A) Grants Read/Write/Execute to Owner, Read/Execute to Group, and Read to Others
- B) Grants Read/Write to Owner, Execute to Group, and Write to Others
- C) Deletes the file
- D) Changes the ownership of the file
- **Answer: ✅ A**
- **Explanation**: 
  - `7` (owner) = $4+2+1$ (rwx).
  - `5` (group) = $4+0+1$ (r-x).
  - `4` (others) = $4+0+0$ (r--).

#### Q36. Which command is used to display currently running processes in a Linux terminal?
- A) `ls`
- B) `df`
- C) `ps`
- D) `grep`
- **Answer: ✅ C**
- **Explanation**: `ps` (process status) displays active processes. `top` is also used for a real-time view.

#### Q37. To search for a specific text pattern inside files in a Linux system, which tool is used?
- A) `find`
- B) `grep`
- C) `du`
- D) `chmod`
- **Answer: ✅ B**
- **Explanation**: `grep` searches files for matching text lines using regular expressions.

---

## 🔷 Topic 7: Practice Conceptual Checkups

#### Q38. In a timeshare OS, what happens when a process's assigned time slice expires?
- A) It is terminated
- B) It transitions from Running to Ready
- C) It transitions from Running to Waiting
- D) It enters a deadlocked state
- **Answer: ✅ B**
- **Explanation**: When the quantum expires, the OS generates a timer interrupt, preempting the process from the CPU and placing it back in the Ready queue.

#### Q39. What is a system call?
- A) A hardware diagnostic function
- B) A program translation tool like a compiler
- C) The interface used by user-space applications to request services from the kernel
- D) An IPC network protocol
- **Answer: ✅ C**
- **Explanation**: System calls act as API interfaces between user programs and Kernel operations.

#### Q40. Which necessary condition of deadlock is broken if we share access to a database table for reading?
- A) Mutual Exclusion
- B) Hold and Wait
- C) No Preemption
- D) Circular Wait
- **Answer: ✅ A**
- **Explanation**: Read-only databases do not require exclusive lock access, breaking Mutual Exclusion.

#### Q41. In contiguous file allocation, the biggest drawback is:
- A) No support for direct access
- B) Huge directory structure overhead
- C) External fragmentation and file size growth issues
- D) Slow execution speed
- **Answer: ✅ C**
- **Explanation**: Contiguous allocation requires finding contiguous free blocks. This leads to external fragmentation over time and limits a file's ability to grow if adjacent blocks are occupied.

#### Q42. Which RAID level distributes striping and parity blocks across all disks (requiring at least 3 disks)?
- A) RAID 1
- B) RAID 5
- C) RAID 6
- D) RAID 0
- **Answer: ✅ B**
- **Explanation**: RAID 5 stripes data and distributes parity blocks across all disks, allowing recovery from a single drive crash.

#### Q43. What is the Belady's Anomaly condition?
- A) CPU utilization drops below 50%
- B) Page faults increase as physical frames increase (in FIFO)
- C) Mutex locks are held permanently
- D) Memory leaks crash the system
- **Answer: ✅ B**
- **Explanation**: It describes the anomaly where a larger memory frame pool leads to more page fault interrupts under FIFO.

#### Q44. The logical address space is mapped to physical address space at runtime by which hardware component?
- A) CPU Scheduler
- B) Memory Management Unit (MMU)
- C) Cache controller
- D) Disk Controller
- **Answer: ✅ B**
- **Explanation**: The MMU is the physical hardware circuit that translates virtual/logical addresses to physical RAM addresses.

#### Q45. Which of the following commands is used to display disk usage statistics in human-readable format?
- A) `df -h`
- B) `du -s`
- C) `top`
- D) `free`
- **Answer: ✅ A**
- **Explanation**: `df -h` reports disk space usage for all mounted file systems in human-readable terms (e.g., GB, MB).

#### Q46. What does the system call `exec()` do?
- A) Spawns a child process
- B) Replaces the current process's memory space with a new executable program
- C) Terminates the process
- D) Blocks execution until child finishes
- **Answer: ✅ B**
- **Explanation**: Unlike `fork()`, which creates a new process, `exec()` overwrites the calling process's memory space, registers, and stack with a new program.

#### Q47. The critical section problem is solved by Peterson's solution for how many processes?
- A) Exactly 2
- B) $N$ processes
- C) Infinite processes
- D) 1 process
- **Answer: ✅ A**
- **Explanation**: Peterson's algorithm is restricted to exactly two processes sharing a critical section.

#### Q48. Which memory type has the fastest access time?
- A) Cache memory
- B) Hard Disk
- C) CPU Registers
- D) RAM
- **Answer: ✅ C**
- **Explanation**: Registers are located directly inside the CPU, making their access speeds faster than cache (L1/L2/L3) and main memory.

#### Q49. A scheduler that selects which processes should be brought into the ready queue from disk is called:
- A) Short-term scheduler (CPU Scheduler)
- B) Long-term scheduler (Job Scheduler)
- C) Medium-term scheduler
- D) Dispatcher
- **Answer: ✅ B**
- **Explanation**: The long-term scheduler controls the degree of multiprogramming by loading processes from disk into RAM.

#### Q50. In a Resource Allocation Graph, a directed edge from a Resource ($R$) to a Process ($P$) represents:
- A) Process $P$ requesting Resource $R$
- B) Resource $R$ allocated to Process $P$
- C) Deadlocked resource
- D) Process $P$ releasing Resource $R$
- **Answer: ✅ B**
- **Explanation**: A directed edge from resource to process ($R \to P$) is an **assignment edge**. An edge from process to resource ($P \to R$) is a **request edge**.
