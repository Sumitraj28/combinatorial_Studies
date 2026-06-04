# Unit III: DBMS - MCQ Bank

Master database systems, SQL commands, normalization math, and transactions with these 50 solved, high-probability Multiple Choice Questions.

---

## 🔷 Topic 1: DBMS Architecture & Keys

#### Q1. Which layer of the Three-Schema architecture defines the physical file organization, data paths, and index storage?
- A) Conceptual Level
- B) External Level
- C) Internal Level
- D) Logical Level
- **Answer: ✅ C**
- **Explanation**: The internal (physical) level describes how the data is stored in memory and on disk.

#### Q2. The ability to modify the conceptual schema without having to rewrite user applications or external views is called:
- A) Physical Data Independence
- B) Logical Data Independence
- C) Database Redundancy
- D) Multi-user Concurrency
- **Answer: ✅ B**
- **Explanation**: Logical data independence isolates the external views from conceptual changes. Physical data independence isolates conceptual schemas from physical storage modifications.

#### Q3. In a table named `Employees` with 5 columns and 100 rows, what is the degree and cardinality of the relation?
- A) Degree = 100, Cardinality = 5
- B) Degree = 5, Cardinality = 100
- C) Degree = 5, Cardinality = 5
- D) Degree = 100, Cardinality = 100
- **Answer: ✅ B**
- **Explanation**: Degree is the number of attributes (columns), which is 5. Cardinality is the number of tuples (rows), which is 100.

#### Q4. A minimal super key is formally defined as:
- A) Primary Key
- B) Foreign Key
- C) Candidate Key
- D) Alternate Key
- **Answer: ✅ C**
- **Explanation**: A candidate key is a super key that has no proper subsets that are also super keys. It is the minimal set of attributes needed to uniquely identify a row.

#### Q5. Which of the following is true regarding Primary Keys and Foreign Keys?
- A) Primary keys can be null, but foreign keys cannot
- B) A table can have multiple primary keys but only one foreign key
- C) Primary keys cannot contain null values, whereas foreign keys can contain null values
- D) Foreign keys must reference the primary key of the same table
- **Answer: ✅ C**
- **Explanation**: Primary keys enforce entity integrity and cannot be null. Foreign keys enforce referential integrity and can contain null values unless explicitly declared `NOT NULL`.

#### Q6. A relation has 4 attributes: $A, B, C, D$. The only candidate key is $A$. How many possible super keys exist?
- A) 4
- B) 8
- C) 16
- D) 2
- **Answer: ✅ B**
- **Explanation**: Since $A$ is the candidate key, any set of attributes containing $A$ is a super key. The remaining attributes are $B, C, D$ (3 attributes). The number of combinations is $2^3 = 8$.

---

## 🔷 Topic 2: SQL Commands & Joins

#### Q7. Which SQL command belongs to the Data Definition Language (DDL)?
- A) `UPDATE`
- B) `GRANT`
- C) `TRUNCATE`
- D) `COMMIT`
- **Answer: ✅ C**
- **Explanation**: `TRUNCATE` defines/resets storage structures, making it DDL. `UPDATE` is DML, `GRANT` is DCL, and `COMMIT` is TCL.

#### Q8. The difference between `DELETE` and `TRUNCATE` is:
- A) `DELETE` removes the table structure, while `TRUNCATE` only removes rows
- B) `TRUNCATE` is a DML command and can be rolled back
- C) `DELETE` removes rows one-by-one and is logged, whereas `TRUNCATE` deallocates data pages and is faster
- D) `DELETE` cannot use a `WHERE` clause
- **Answer: ✅ C**
- **Explanation**: `DELETE` is a logged, row-by-row DML command. `TRUNCATE` is a DDL command that clears all rows in bulk by deallocating data pages, bypassing individual row logging.

#### Q9. Which clause is used to filter records after they have been grouped by an aggregate function?
- A) `WHERE`
- B) `HAVING`
- C) `ORDER BY`
- D) `SELECT`
- **Answer: ✅ B**
- **Explanation**: `WHERE` filters rows before grouping. `HAVING` filters group values computed by aggregate functions.

#### Q10. Consider the query:
`SELECT dept_name, ID, avg(salary) FROM instructor GROUP BY dept_name;`
Why does this query return an error in SQL?
- A) Average salary cannot be calculated
- B) The column `ID` is selected but not included in the `GROUP BY` clause or an aggregate function
- C) `dept_name` cannot be grouped
- D) The `FROM` clause is invalid
- **Answer: ✅ B**
- **Explanation**: Any column present in the `SELECT` list must either be part of an aggregate function (e.g., `avg(salary)`) or appear in the `GROUP BY` clause. Since `ID` is neither, the database engine cannot determine how to display it.

#### Q11. Which type of join returns all records from the left table and the matching records from the right table, filling unmatched right fields with `NULL`?
- A) Inner Join
- B) Full Outer Join
- C) Left Outer Join
- D) Cross Join
- **Answer: ✅ C**
- **Explanation**: A `LEFT OUTER JOIN` returns all records from the left table plus matching right-table records. Unmatched right-side fields return `NULL`.

---

## 🔷 Topic 3: Database Normalization

#### Q12. A relation is in First Normal Form (1NF) if:
- A) It has no composite keys
- B) All non-key columns depend on the primary key
- C) All attribute values are atomic
- D) It has no transitive dependencies
- **Answer: ✅ C**
- **Explanation**: 1NF requires that domains contain only atomic (indivisible) values, and no table column contains multi-valued attributes or repeating groups.

#### Q13. Partial dependency in a relation occurs when:
- A) A non-key attribute depends on another non-key attribute
- B) A non-key attribute depends on only a part of a composite primary key
- C) The primary key depends on a foreign key
- D) The relation is in 3NF
- **Answer: ✅ B**
- **Explanation**: Partial dependencies occur when a non-prime attribute is functionally dependent on a subset of a candidate key. This is resolved by converting the relation to 2NF.

#### Q14. Transitive dependency ($A \to B \to C$) is eliminated in which normal form?
- A) 2NF
- B) 3NF
- C) BCNF
- D) 4NF
- **Answer: ✅ B**
- **Explanation**: 3NF eliminates transitive dependencies (where a non-prime attribute determines another non-prime attribute).

#### Q15. A relation $R(A, B, C)$ has functional dependencies $AB \to C$ and $C \to A$. The candidate keys are $\{A, B\}$ and $\{B, C\}$. In which normal form is $R$?
- A) 1NF
- B) 2NF
- C) 3NF
- D) BCNF
- **Answer: ✅ C**
- **Explanation**: 
  - For $AB \to C$: $AB$ is a super key. (Valid for BCNF and 3NF).
  - For $C \to A$: $C$ is not a super key, but $A$ is a prime attribute (part of candidate key $\{A, B\}$).
  - Since $C \to A$ does not have a super key on the left, it violates BCNF. However, because the right side ($A$) is prime, it satisfies the 3NF condition. Thus, the relation is in 3NF.

#### Q16. Which normal form does NOT guarantee dependency preservation?
- A) 2NF
- B) 3NF
- C) BCNF
- D) 1NF
- **Answer: ✅ C**
- **Explanation**: While BCNF is stricter and resolves redundancy anomalies better than 3NF, decomposing a relation into BCNF can sometimes prevent functional dependencies from being preserved.

---

## 🔷 Topic 4: Transaction & Concurrency Control

#### Q17. The ACID property that ensures a transaction is processed in its entirety or not at all (All-or-Nothing) is:
- A) Consistency
- B) Isolation
- C) Atomicity
- D) Durability
- **Answer: ✅ C**
- **Explanation**: Atomicity guarantees that if any part of a transaction fails, the entire transaction is rolled back.

#### Q18. Which database component is responsible for enforcing the Isolation property?
- A) Recovery Manager
- B) Concurrency Control Manager
- C) Buffer Manager
- D) File Manager
- **Answer: ✅ B**
- **Explanation**: The Concurrency Control Manager uses locking, timestamping, or validation to ensure concurrent transactions execute in isolation without interfering with one another.

#### Q19. A transaction has completed its final programming statement but its changes are only saved in RAM buffers and not yet committed to disk. What state is this transaction in?
- A) Active
- B) Committed
- C) Partially Committed
- D) Failed
- **Answer: ✅ C**
- **Explanation**: The transaction enters the "Partially Committed" state after executing its last write statement. It transition to "Committed" only after the log records are written to non-volatile disk.

#### Q20. If a precedence graph built from a concurrent schedule contains a cycle, what does this indicate?
- A) The schedule has a deadlock
- B) The schedule is not conflict-serializable
- C) The schedule is view-serializable
- D) The transaction will commit successfully
- **Answer: ✅ B**
- **Explanation**: A precedence graph (serialization graph) has a cycle if and only if the schedule is not conflict-serializable.

#### Q21. The Two-Phase Locking (2PL) protocol ensures:
- A) Deadlock-free transactions
- B) Conflict-serializable schedules
- C) Durability
- D) High database performance
- **Answer: ✅ B**
- **Explanation**: 2PL guarantees that any execution schedule is conflict-serializable. However, it does not prevent deadlocks.

#### Q22. In Two-Phase Locking (2PL), a transaction can acquire locks but cannot release any during the:
- A) Shrinking Phase
- B) Growing Phase
- C) Commit Phase
- D) Active Phase
- **Answer: ✅ B**
- **Explanation**: In the Growing Phase, a transaction may obtain locks but is forbidden from releasing any. In the Shrinking Phase, locks can only be released.

---

## 🔷 Topic 5: NoSQL & Big Data

#### Q23. What does the term NoSQL stand for?
- A) No Structured Query Language
- B) Not Only SQL
- C) Network Object SQL
- D) Non-relational SQL
- **Answer: ✅ B**
- **Explanation**: NoSQL stands for "Not Only SQL," highlighting databases that extend beyond traditional relational models.

#### Q24. Which of the following is a Document-based NoSQL database?
- A) Redis
- B) MongoDB
- C) Neo4j
- D) Cassandra
- **Answer: ✅ B**
- **Explanation**: MongoDB stores data as JSON-like documents. Redis is Key-Value, Neo4j is Graph, and Cassandra is Column-Family.

#### Q25. According to the CAP Theorem, a distributed database system can guarantee at most which properties concurrently?
- A) Consistency and Availability only
- B) Consistency, Availability, and Partition Tolerance
- C) Any two of: Consistency, Availability, and Partition Tolerance
- D) Partition Tolerance only
- **Answer: ✅ C**
- **Explanation**: The CAP theorem states that a distributed system can guarantee at most two of the three properties: Consistency, Availability, and Partition Tolerance.

#### Q26. NoSQL databases prioritize which set of properties over traditional ACID?
- A) BASE (Basically Available, Soft State, Eventual Consistency)
- B) SOAP
- C) RAID
- D) FIFO
- **Answer: ✅ A**
- **Explanation**: NoSQL databases trade strict ACID consistency for BASE (Basically Available, Soft State, Eventual Consistency) to scale horizontally.

---

## 🔷 Topic 6: General Database Review

#### Q27. What is metadata?
- A) Large aggregated data arrays
- B) Data describing other data (logical schema, table descriptions, etc.)
- C) Backed up database files
- D) Private encryption keys
- **Answer: ✅ B**
- **Explanation**: Metadata is data that describes database structure (e.g., table schemas, column types, stored in the data dictionary).

#### Q28. Which index structure is best optimized for handling SQL range queries (e.g., `WHERE age BETWEEN 20 AND 30`)?
- A) Hash Index
- B) B+ Tree Index
- C) Bitmap Index
- D) Dense Index
- **Answer: ✅ B**
- **Explanation**: B+ Trees keep all actual data pointers in leaf nodes linked sequentially, making range traversals extremely fast. Hash indexes are optimized for exact match lookups (`=`) but slow for range scans.

#### Q29. How many clustered indexes can be created on a single table?
- A) 1
- B) Unlimited
- C) 5
- D) None
- **Answer: ✅ A**
- **Explanation**: A clustered index determines the physical order of data rows on disk. Since data can only be sorted one way, a table can have only one clustered index.

#### Q30. Relational Algebra is a __________ query language, whereas SQL is a __________ query language.
- A) Declarative, Procedural
- B) Procedural, Declarative
- C) Compiler, Interpreter
- D) Logical, Physical
- **Answer: ✅ B**
- **Explanation**: Relational Algebra is procedural (defines the step-by-step operations to fetch data). SQL is declarative (defines *what* data to retrieve, leaving the execution steps to the query optimizer).

#### Q31. In SQL, the default constraint that ensures a foreign key references a valid primary key is:
- A) Domain Integrity
- B) Referential Integrity
- C) Entity Integrity
- D) User-defined Integrity
- **Answer: ✅ B**
- **Explanation**: Referential integrity prevents orphan rows by ensuring child foreign keys point to valid parent primary keys.

#### Q32. What is the Cartesian Product ($\times$) of a relation $R$ with 3 rows and a relation $S$ with 4 rows?
- A) 7 rows
- B) 12 rows
- C) 1 row
- D) 0 rows
- **Answer: ✅ B**
- **Explanation**: The Cartesian product generates all possible row pairings: $\text{Rows} = |R| \times |S| = 3 \times 4 = 12$.

#### Q33. Which SQL command rollback transaction checkpoints?
- A) `COMMIT`
- B) `ROLLBACK`
- C) `SAVEPOINT`
- D) `REVOKE`
- **Answer: ✅ B**
- **Explanation**: `ROLLBACK` reverts modifications made by a transaction, either to the start or to a defined `SAVEPOINT`.

#### Q34. What is the oldest database model?
- A) Relational Model
- B) Network Model
- C) Hierarchical Model
- D) Object-Oriented Model
- **Answer: ✅ C**
- **Explanation**: The Hierarchical model (organizing data in tree-like parent-child parent structures) is the oldest database model.

#### Q35. A lossy join decomposition is one where:
- A) Data is deleted during normalization
- B) Joining decomposed tables yields extra spurious tuples that were not in the original relation
- C) The primary key is deleted
- D) Columns are renamed
- **Answer: ✅ B**
- **Explanation**: "Lossy" does not mean data loss. It means information is lost because joining the decomposed relations creates extra spurious tuples, corrupting the original data structure.

#### Q36. In DBMS, the buffer manager acts to:
- A) Parse incoming SQL text
- B) Cache pages read from disk in main memory to speed up access times
- C) Lock transactions
- D) Format tables
- **Answer: ✅ B**
- **Explanation**: The buffer manager manages cache memory, fetching database pages into RAM and choosing which ones to swap out when RAM is full.

#### Q37. In functional dependency notation, if $X \to Y$ and $Y \to Z$, then $X \to Z$ is derived using:
- A) Reflexivity Rule
- B) Augmentation Rule
- C) Transitivity Rule
- D) Decomposition Rule
- **Answer: ✅ C**
- **Explanation**: This is the Transitivity Rule, one of Armstrong's axioms.

#### Q38. A composite key is:
- A) A key containing encrypted columns
- B) A primary or candidate key that consists of more than one attribute
- C) A key that references multiple tables
- D) An alternate key
- **Answer: ✅ B**
- **Explanation**: A composite key is a key made up of multiple columns.

#### Q39. What is a transaction schedule?
- A) A chronologically ordered sequence of operations from concurrent transactions
- B) A list of daily backups
- C) The priority queue of the CPU scheduler
- D) The physical disk block layout
- **Answer: ✅ A**
- **Explanation**: A schedule represents the execution order of operations (reads, writes, commits, rollbacks) from concurrent transactions.

#### Q40. Which lock type allows multiple transactions to read a database row simultaneously but prevents updates?
- A) Exclusive Lock (X)
- B) Shared Lock (S)
- C) Intent Lock (I)
- D) Binary Lock
- **Answer: ✅ B**
- **Explanation**: Shared locks (S) allow multiple read operations. Exclusive locks (X) grant write access to a single transaction, blocking all others.

#### Q41. In database recovery, the Write-Ahead Logging (WAL) protocol states:
- A) Writes to the database can happen before log entries are written
- B) Log records representing a database modification must be written to disk before the actual database page is updated on disk
- C) Logging is done only at transaction commit
- D) Logs are written to RAM only
- **Answer: ✅ B**
- **Explanation**: WAL ensures that log entries are saved to non-volatile disk before dirty database pages are written. This guarantees the system can recover from crashes mid-write.

#### Q42. The process of viewing a data cube across a single fixed attribute value is called:
- A) Dicing
- B) Pivoting
- C) Slicing
- D) Drill-down
- **Answer: ✅ C**
- **Explanation**: Slicing selects a single dimension from a data cube, producing a sub-cube.

#### Q43. What does SQL stand for?
- A) Standard Query Language
- B) Sequential Query Language
- C) Structured Query Language
- D) System Query Language
- **Answer: ✅ C**
- **Explanation**: SQL stands for Structured Query Language.

#### Q44. A table has functional dependencies $A \to B$ and $C \to D$. If we decompose it into $R_1(A, B)$ and $R_2(C, D)$, this decomposition is:
- A) Dependency Preserving
- B) Lossy
- C) Invalid
- D) Non-dependency preserving
- **Answer: ✅ A**
- **Explanation**: Since all original functional dependencies ($A \to B$ and $C \to D$) can be checked within their respective relations ($R_1$ and $R_2$), the decomposition is dependency preserving.

#### Q45. Which normal form is adequate for most standard commercial database designs?
- A) 1NF
- B) 3NF
- C) 5NF
- D) BCNF
- **Answer: ✅ B**
- **Explanation**: 3NF is widely considered a balanced target for business databases because it eliminates most anomalies while guaranteeing dependency preservation.

#### Q46. What does a database catalog contain?
- A) The raw table rows
- B) Schema metadata and index mappings
- C) Transaction logs
- D) SQL execution scripts
- **Answer: ✅ B**
- **Explanation**: The catalog (data dictionary) stores metadata describing the database's schema, structure, tables, and views.

#### Q47. The commit command ensures which ACID property?
- A) Isolation
- B) Consistency
- C) Durability
- D) Atomicity
- **Answer: ✅ C**
- **Explanation**: `COMMIT` writes transaction log records to disk, making changes permanent (durable) and immune to crashes.

#### Q48. In PL/SQL, a database trigger is:
- A) A manual query script
- B) A stored procedure that executes automatically in response to DDL/DML events
- C) A type of table index
- D) A transaction lock
- **Answer: ✅ B**
- **Explanation**: A trigger is a block of code that is automatically executed (fired) by the database engine in response to events like `INSERT`, `UPDATE`, or `DELETE`.

#### Q49. Which of the following is NOT an aggregate function in SQL?
- A) `COUNT()`
- B) `AVG()`
- C) `SUM()`
- D) `SELECT()`
- **Answer: ✅ D**
- **Explanation**: `SELECT` is a core query keyword. Aggregate functions compute single values over columns, such as `COUNT()`, `AVG()`, and `SUM()`.

#### Q50. If $X \to Y$ holds in a relation, we can say:
- A) Y uniquely determines X
- B) X uniquely determines Y
- C) X and Y are candidate keys
- D) Y is a prime attribute
- **Answer: ✅ B**
- **Explanation**: $X \to Y$ is a functional dependency, stating that attribute $X$ uniquely determines the value of attribute $Y$.
