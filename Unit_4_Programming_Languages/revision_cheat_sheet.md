# Unit IV: PL Revision Cheat Sheet

A rapid-revision summary of language fundamentals, pointers, OOP principles, and memory bindings.

---

## ⚡ 1. Memory Layout & Storage Classes Card

### C/C++ Storage Classes Quick Reference
*   **`auto`**: Default. Stack allocation. Destroyed on block exit.
*   **`register`**: Allocated in CPU registers. Faster access, but cannot use reference address-of operator (`&`) in C.
*   **`static`**: Retains value. Initialized once. Stored in data segment, stays active until program termination.
*   **`extern`**: Variable declared elsewhere (global context).

### Stack vs. Heap Memory Allocation
| Attribute | Stack Memory | Heap Memory |
| :--- | :--- | :--- |
| **Allocation** | Automatic (handled by compiler). | Manual (via `new`/`delete` or Jvm GC). |
| **Speed** | Extremely fast (pointer adjustments). | Slower (overhead of search/fragmentation). |
| **Size Limit** | Small, fixed size (leads to `StackOverflow`).| Very large, bounded by system RAM. |
| **Order** | Strict LIFO order. | Arbitrary allocation/free order. |

---

## 📊 2. High-Yield Comparison Tables

### Abstract Class vs. Interface
| Feature | Abstract Class | Interface |
| :--- | :--- | :--- |
| **Inheritance** | Single class inheritance (use `extends`).| Multiple implementations allowed (`implements`). |
| **Methods** | Can contain both abstract & concrete methods.| All abstract (default methods in Java 8+). |
| **Variables** | Any type (instance variables allowed). | Must be `public static final` constants. |
| **Constructor** | Has constructors (called by subclasses). | Does not have constructors. |
| **Speed** | Faster function dispatch. | Slower due to dynamic interface lookup. |

### C++ vs. Java OOP Models
| Feature | C++ | Java |
| :--- | :--- | :--- |
| **Multiple Inheritance**| **Yes** (directly supported). | **No** (Only via interfaces). |
| **Memory Cleanup** | Manual Destructor (`~ClassName()`). | Automatic Garbage Collector. |
| **Pointers** | Supported (`*ptr`, pointer arithmetic). | Hidden references. No pointer arithmetic. |
| **Virtual by Default** | **No** (Must declare functions as `virtual`).| **Yes** (All non-static methods are virtual). |

---

## 🧠 3. Memory Tricks & Mnemonics

*   **OOP 4 Pillars**: **E-A-I-P** (like "Ape")
    *   **E**ncapsulation, **A**bstraction, **I**nheritance, **P**olymorphism.
*   **SOLID Principles**: **S-O-L-I-D**
    *   **S**ingle Responsibility, **O**pen-Closed, **L**iskov Substitution, **I**nterface Segregation, **D**ependency Inversion.
*   **Java Exception Blocks**: **T-C-F** (like "TCF")
    *   **T**ry, **C**atch, **F**inally.

---

## 🚨 4. High-Risk Confusion Zones

### 1. Method Overloading vs. Method Overriding
*   **Overloading**: Compile-time (static) polymorphism. Same function name, different parameter lists. In the same class scope.
*   **Overriding**: Runtime (dynamic) polymorphism. Same function name and same parameters. Occurs in parent and child classes.

### 2. Pointer vs. Reference in C++
*   **Pointer**: A variable holding an address. Can be reassigned, can point to `NULL`, supports pointer arithmetic (`ptr++`).
*   **Reference**: A constant alias. Cannot be reassigned, cannot be `NULL`, initialized upon declaration.

### 3. Struct vs. Class in C++
*   **`struct`**: Default access modifier is `public`.
*   **`class`**: Default access modifier is `private`.

---

## ⚠️ 5. Traps & Mistakes to Avoid in Exams

*   **Finally block execution**: In Java, the `finally` block **always** executes, even if there is a `return` statement inside the `try` or `catch` block. The only exception is if the system exits via `System.exit()`.
*   **Constructor calling order**: During inheritance, base constructors execute **before** derived constructors. However, destructors execute in the **reverse** order: derived destructors execute before base destructors.
*   **Function Signature**: Overloading is resolved based on the parameter list (type, order, and count) and **not** on the return type. Declaring two functions with the same parameters but different return types will fail compilation.
*   **Virtual Destructor Trap**: In C++, if a base class pointer deletes a derived class object, the base class **must** have a `virtual destructor` (`virtual ~Base()`). Otherwise, only the base destructor will be called, causing memory leaks for the derived portion of the object.
