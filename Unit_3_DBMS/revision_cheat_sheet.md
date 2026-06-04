# Unit III: DBMS Revision Cheat Sheet

A quick-revision guide for Database Management Systems concepts, SQL commands, and transaction math.

---

## ⚡ 1. DBMS Formulas & Key Rules

### Super Keys Calculations
Let a relation $R$ have $n$ attributes: $A_1, A_2, \dots, A_n$.
*   **Case 1: One Candidate Key**: If the only candidate key is a single attribute (e.g., $A_1$), the number of possible super keys is:
    $$\text{Super Keys} = 2^{n-1}$$
*   **Case 2: Composite Candidate Key**: If the only candidate key is a composite of $k$ attributes (e.g., $\{A_1, A_2\}$ where $k=2$), the number of possible super keys is:
    $$\text{Super Keys} = 2^{n-k}$$
*   **Case 3: Two Separate Candidate Keys**: If there are two candidate keys $K_1$ and $K_2$:
    $$\text{Super Keys} = \text{Super Keys from } K_1 + \text{Super Keys from } K_2 - \text{Super Keys from } (K_1 \cup K_2)$$
    $$\text{Super Keys} = 2^{n-|K_1|} + 2^{n-|K_2|} - 2^{n-|K_1 \cup K_2|}$$

### ACID Property Subsystem Mapping
*   **A**tomicity $\to$ Managed by the **Recovery Manager** (Undo Logs).
*   **C**onsistency $\to$ Managed by the **Compiler & Runtime Constraints** (Integrity constraints).
*   **I**solation $\to$ Managed by the **Concurrency Control Manager** (Locking/Timestamping).
*   **D**urability $\to$ Managed by the **Recovery Manager** (Redo Logs).

---

## 📊 2. High-Yield Summary Tables

### SQL Command Classifications
| Category | Category Name | Key Commands | Transactional? |
| :--- | :--- | :--- | :--- |
| **DDL** | Data Definition Language | `CREATE`, `ALTER`, `DROP`, `TRUNCATE`, `RENAME` | **No** (Auto-commits in most engines) |
| **DML** | Data Manipulation Language | `SELECT`, `INSERT`, `UPDATE`, `DELETE` | **Yes** (Requires commit/rollback) |
| **DCL** | Data Control Language | `GRANT`, `REVOKE` | **No** |
| **TCL** | Transaction Control Language| `COMMIT`, `ROLLBACK`, `SAVEPOINT` | Controls others |

### Normalization Criteria Summary
| Normal Form | Structural Requirement | Checks for... |
| :--- | :--- | :--- |
| **1NF** | Atomic attribute values (no arrays/multivalues).| Repeating values in cells. |
| **2NF** | In 1NF + No partial dependencies ($X \to Y$ where $X \subset \text{Composite PK}$). | Non-key depending on *part* of primary key. |
| **3NF** | In 2NF + No transitive dependencies ($X \to Y \to Z$ where $Y, Z \notin \text{Keys}$). | Non-key depending on *another* non-key. |
| **BCNF** | For every non-trivial $X \to Y$, $X$ must be a Super Key. | Prime attribute depending on a non-key. |

---

## 🧠 3. Memory Tricks & Mnemonics

*   **Normalization Rules**: **A-K-N-D** (pronounce: "A-Kind")
    *   **A**tomic values (1NF)
    *   **K**ey dependence - No Partial (2NF)
    *   **N**on-key independence - No Transitive (3NF)
    *   **D**eterminant must be Super Key (BCNF)
*   **Transactional SQL Commands**: **C-R-S** (like "Cars")
    *   **C**ommit, **R**ollback, **S**avepoint.
*   **Relational Algebra Operations**: **S-P-J** (like "SPaJ")
    *   **S**election ($\sigma$ - Rows), **P**rojection ($\pi$ - Columns), **J**oin ($\bowtie$ - Merge).

---

## 🚨 4. High-Risk Confusion Zones

### 1. `DELETE` vs. `TRUNCATE`
*   **`DELETE`**: DML command. Removes specified rows using `WHERE`. It logs each deleted row, making it slow but allowing recovery via `ROLLBACK`.
*   **`TRUNCATE`**: DDL command. Drops the entire table space and recreates an empty version. It does not log individual row deletions, making it much faster but preventing standard rollback.

### 2. `WHERE` vs. `HAVING`
*   **`WHERE`**: Filters records **before** groups are formed. Cannot contain aggregate functions (`SUM`, `AVG`, etc.).
*   **`HAVING`**: Filters groups **after** the `GROUP BY` clause is evaluated. Used exclusively to filter aggregates.

### 3. 3NF vs. BCNF
*   **3NF**: A relation is in 3NF if for $X \to Y$, either $X$ is a super key or $Y$ is a prime attribute. 3NF **always** guarantees dependency preservation.
*   **BCNF**: Stricter. For $X \to Y$, $X$ **must** be a super key. BCNF **does not** guarantee dependency preservation.

---

## ⚠️ 5. Traps & Mistakes to Avoid in Exams

*   **Subnetting/Database mix-up**: Ensure you don't confuse transaction states. A transaction in the *Partially Committed* state has completed its last statement, but its changes are only write-cached in RAM and not yet durable on disk.
*   **Candidate Key counting**: When finding candidate keys, attributes that only appear on the right side of functional dependencies can never be part of a candidate key. Attributes that never appear on the right side of any dependency **must** be part of every candidate key.
*   **GROUP BY rule**: In a `SELECT` statement containing a `GROUP BY` clause, any attribute in the SELECT list that is not part of an aggregate function **must** be listed in the `GROUP BY` clause. Otherwise, the query will fail.
