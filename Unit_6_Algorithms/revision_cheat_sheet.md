# Unit VI: Algorithms Revision Cheat Sheet

A quick study sheet summarizing sorting complexities, Master Theorem rules, and core algorithm comparisons.

---

## ⚡ 1. Master Theorem & Complexity Card

### Master Theorem Recurrence Solver
Given $T(N) = aT(N/b) + \Theta(N^d)$ where $a \ge 1, b > 1, d \ge 0$:

| Condition | Time Complexity Solution | Case Name |
| :--- | :--- | :--- |
| **$d < \log_b a$** | $T(N) = \Theta(N^{\log_b a})$ | Case 1 (Recursive work dominates) |
| **$d = \log_b a$** | $T(N) = \Theta(N^d \log N)$ | Case 2 (Work is equal at all levels) |
| **$d > \log_b a$** | $T(N) = \Theta(N^d)$ | Case 3 (Split/combine work dominates) |

### Asymptotic Hierarchy
$$O(1) < O(\log N) < O(N) < O(N \log N) < O(N^2) < O(N^3) < O(2^N) < O(N!)$$

---

## 📊 2. High-Yield Summary Tables

### Graph Algorithms Time Complexity Benchmark
| Algorithm | Goal | Time Complexity | Strategy |
| :--- | :--- | :--- | :--- |
| **Dijkstra** | Single-Source Shortest Path (no negative weights) | $O((V+E)\log V)$ | Greedy |
| **Bellman-Ford** | Single-Source Shortest Path (supports negative weights) | $O(V \cdot E)$ | Dynamic Programming |
| **Floyd-Warshall**| All-Pairs Shortest Path | $O(V^3)$ | Dynamic Programming |
| **Kruskal's** | Minimum Spanning Tree (MST) | $O(E \log E)$ | Greedy (uses Union-Find) |
| **Prim's** | Minimum Spanning Tree (MST) | $O((V+E)\log V)$ | Greedy (uses Heap) |

### Dynamic Programming vs. Greedy Strategy
| Feature | Dynamic Programming | Greedy Strategy |
| :--- | :--- | :--- |
| **Choice Order** | Evaluates all subproblems before choosing. | Makes local optimal choice immediately.|
| **Optimal Substructure**| Yes. | Yes. |
| **Subproblem Overlap** | **Yes** (essential). | **No** (often independent choices). |
| **Backtracking** | Yes (computes and compares branches). | No (once choice is made, it is final). |
| **Efficiency** | Generally slower ($O(N^2)$ or $O(N^3)$). | Generally fast ($O(N)$ or $O(N \log N)$). |

---

## 🧠 3. Memory Tricks & Mnemonics

*   **Dynamic Programming Characteristics**: **O-O**
    *   **O**ptimal Substructure, **O**verlapping Subproblems.
*   **Divide & Conquer Steps**: **D-C-C**
    *   **D**ivide, **C**onquer, **C**ombine.
*   **Asymptotic bounds**:
    *   **O** $\to$ **O**utside / **O**ver (Upper bound).
    *   $\Omega$ (Omega) $\to$ **O**n/Under (Lower bound).
    *   $\Theta$ (Theta) $\to$ **T**ight (Average/exact bound).

---

## 🚨 4. High-Risk Confusion Zones

### 1. 0/1 Knapsack vs. Fractional Knapsack
*   **0/1 Knapsack**: Items cannot be split; you either take an item or leave it. This cannot be solved optimally using a Greedy algorithm (must use Dynamic Programming: $O(NW)$ time).
*   **Fractional Knapsack**: Items can be split (e.g., powders/liquids). This is solved optimally using a Greedy algorithm by sorting items by value-to-weight ratio ($O(N \log N)$ time).

### 2. Dijkstra vs. Bellman-Ford
*   **Dijkstra**: Faster, but fails if the graph contains negative edge weights.
*   **Bellman-Ford**: Slower, but handles negative edge weights and detects **negative weight cycles**.

### 3. Memoization vs. Tabulation
*   **Memoization**: Top-down approach. Uses recursion and caches results in a lookup table when computed.
*   **Tabulation**: Bottom-up approach. Fills a table iteratively starting from base cases.

---

## ⚠️ 5. Traps & Mistakes to Avoid in Exams

*   **Quick Sort Worst-Case**: Quick Sort is not always $O(N \log N)$. If the array is already sorted and we pick the first/last element as the pivot, the runtime degrades to $O(N^2)$.
*   **Dijkstra negative weights trap**: Do not assume Dijkstra works with negative edge weights as long as there are no negative cycles. It can still fail due to its greedy nature. Use Bellman-Ford instead.
*   **Master Theorem applicability**: The Master Theorem cannot be used if $a < 1$ (no subproblems), if $b \le 1$ (problem size is not reduced), or if the recurrence contains non-polynomial terms (e.g., $T(N) = 2T(N/2) + N \log N$ requires extended versions).
