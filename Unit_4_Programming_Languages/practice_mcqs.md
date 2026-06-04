# Unit IV: Programming Languages - MCQ Bank

Test your understanding of pointers, storage classes, OOP paradigms, parameter passing, and memory bindings with these 50 solved, high-probability Multiple Choice Questions.

---

## 🔷 Topic 1: Pointers & Storage Classes

#### Q1. What is a pointer in C/C++?
- A) A data type used to store characters
- B) A variable that stores the memory address of another variable
- C) A keyword used to define classes
- D) A standard library template
- **Answer: ✅ B**
- **Explanation**: A pointer holds the raw physical address of a memory location, allowing direct memory manipulation.

#### Q2. What does the `static` keyword accomplish when applied to a local variable inside a C function?
- A) It makes the variable accessible globally across all files
- B) It stores the variable in a CPU register
- C) It retains the variable's value between multiple function calls, initializing it only once
- D) It prevents the variable from being modified
- **Answer: ✅ C**
- **Explanation**: A static local variable is stored in the data segment of RAM rather than the stack. It persists for the lifetime of the program, retaining its value between function call invocations.

#### Q3. Which storage class in C uses CPU registers instead of RAM to store variables, meaning you cannot take their address with the `&` operator?
- A) `auto`
- B) `static`
- C) `register`
- D) `extern`
- **Answer: ✅ C**
- **Explanation**: The `register` storage class requests that the compiler allocate a CPU register for the variable for high-speed operations. Because CPU registers do not have memory addresses, using the address-of operator `&` on a register variable in C will fail.

#### Q4. What is the output of the following C++ code snippet?
```cpp
int x = 10;
int &ref = x;
ref = 20;
cout << x;
```
- A) 10
- B) 20
- C) Compiler Error
- D) Random address value
- **Answer: ✅ B**
- **Explanation**: `ref` is a reference variable, which acts as an alias for `x`. Modifying `ref` modifies `x` directly.

#### Q5. A pointer that stores the address of another pointer variable is called:
- A) Void Pointer
- B) Null Pointer
- C) Double Pointer (Pointer to Pointer)
- D) Dangling Pointer
- **Answer: ✅ C**
- **Explanation**: A double pointer (e.g., `int **ptr`) stores the memory address of an `int*` pointer variable.

---

## 🔷 Topic 2: OOP Principles & Inheritance

#### Q6. Which pillar of Object-Oriented Programming binds data members and member functions together into a single class unit, controlling access via modifiers?
- A) Abstraction
- B) Polymorphism
- C) Encapsulation
- D) Inheritance
- **Answer: ✅ C**
- **Explanation**: Encapsulation is the process of bundling data and methods together and hiding internal details using access specifiers (`private`, `protected`).

#### Q7. The Diamond Problem in multiple inheritance arises when:
- A) A parent class has two child classes
- B) A child class inherits from two parent classes that both derive from a single grandparent class, creating ambiguity
- C) A class has virtual functions
- D) A constructor calls another constructor
- **Answer: ✅ B**
- **Explanation**: If class $D$ inherits from $B$ and $C$, which both inherit from $A$, class $D$ receives duplicate copies of $A$'s members. This causes ambiguity when calling $A$'s functions from $D$.

#### Q8. In C++, how is the Diamond Problem resolved?
- A) Using multiple interfaces
- B) Using virtual inheritance (`class B : virtual public A`)
- C) Using the `extern` keyword
- D) It cannot be resolved in C++
- **Answer: ✅ B**
- **Explanation**: Declaring base classes as `virtual` during inheritance ensures only a single shared instance of the grandparent class is created in the final derived class.

#### Q9. Java resolves the diamond problem in multiple inheritance by:
- A) Supporting virtual inheritance
- B) Restricting multiple inheritance of classes, allowing multiple inheritance only through interfaces
- C) Ignoring the grandparent class
- D) Allowing multiple constructors
- **Answer: ✅ B**
- **Explanation**: Java disallows multiple inheritance of classes (`extends ClassA, ClassB` is illegal). A class can only extend one parent class, though it can implement multiple interfaces.

#### Q10. A class in C++ that contains at least one pure virtual function (e.g., `virtual void draw() = 0;`) is called:
- A) Concrete Class
- B) Interface
- C) Abstract Class
- D) Static Class
- **Answer: ✅ C**
- **Explanation**: An abstract class in C++ cannot be instantiated directly and serves as a blueprint. It must contain at least one pure virtual function.

---

## 🔷 Topic 3: Polymorphism & Binding

#### Q11. Which of the following is an example of compile-time (static) polymorphism?
- A) Method Overriding
- B) Virtual Functions
- C) Method Overloading
- D) Interface Implementation
- **Answer: ✅ C**
- **Explanation**: Method overloading (same method name, different parameters) is resolved by the compiler at compile time, making it compile-time polymorphism.

#### Q12. Runtime polymorphism (dynamic binding) is implemented in C++ using which mechanism?
- A) Templates
- B) Storage Classes
- C) Virtual Functions
- D) Operator Overloading
- **Answer: ✅ C**
- **Explanation**: Declaring a base class function as `virtual` tells the compiler to perform late binding (dynamic lookup) at runtime using VTABLE structures.

#### Q13. In dynamic binding, which compiler-generated structures map virtual function calls to their actual implementations at runtime?
- A) Page Tables
- B) VTABLE and VPTR (Virtual Table and Virtual Pointer)
- C) Symbol Tables
- D) Stack Frames
- **Answer: ✅ B**
- **Explanation**: When a class contains a virtual function, the compiler inserts a virtual pointer (`vptr`) into the object. This pointer points to a virtual table (`vtable`) containing function pointers for the overridden methods.

#### Q14. What is the output of the following C++ code?
```cpp
class Base {
public:
    void show() { cout << "Base "; }
};
class Derived : public Base {
public:
    void show() { cout << "Derived "; }
};
int main() {
    Base *ptr = new Derived();
    ptr->show();
    return 0;
}
```
- A) Base
- B) Derived
- C) Compiler Error
- D) Runtime Crash
- **Answer: ✅ A**
- **Explanation**: Because `show()` is not declared as a `virtual` function in the base class, the compiler performs static binding. Since the pointer type is `Base*`, it calls `Base::show()`.

#### Q15. If we modify the previous question and declare the base class function as `virtual void show()`, what is the output?
- A) Base
- B) Derived
- C) Compiler Error
- D) Base Derived
- **Answer: ✅ B**
- **Explanation**: Adding `virtual` triggers dynamic binding, resolving the call at runtime based on the actual object type (`Derived`), not the pointer type (`Base*`).

---

## 🔷 Topic 4: Parameter Passing & Exceptions

#### Q16. Which parameter passing technique creates a copy of the argument on the function's stack frame?
- A) Pass by Reference
- B) Pass by Address
- C) Pass by Value
- D) Pass by Name
- **Answer: ✅ C**
- **Explanation**: Pass by value copies the argument. Modifications inside the function do not affect the caller's variable.

#### Q17. In Java, what is the parameter passing model for primitive data types and object references?
- A) Primitives are passed by reference, objects by value
- B) All parameters (both primitives and object references) are passed by value
- C) All parameters are passed by reference
- D) Objects are passed by reference, primitives by value
- **Answer: ✅ B**
- **Explanation**: Java is strictly **pass-by-value**. For primitives, it passes a copy of the value. For objects, it passes a copy of the reference address (meaning you can modify the object's fields, but you cannot change which object the caller's reference points to).

#### Q18. What is the execution order of `try`, `catch`, and `finally` blocks in Java if an exception occurs?
- A) `try` $\to$ `finally`
- B) `try` $\to$ `catch` $\to$ `finally`
- C) `catch` $\to$ `finally`
- D) `try` $\to$ `catch`
- **Answer: ✅ B**
- **Explanation**: If an exception occurs in the `try` block, execution jumps to the matching `catch` block. Afterward, the `finally` block executes.

#### Q19. In Java, a `finally` block:
- A) Executes only if no exception occurs
- B) Executes only if an exception is caught
- C) Always executes, even if a `return` statement is executed in `try` or `catch`
- D) Replaces the catch block
- **Answer: ✅ C**
- **Explanation**: The `finally` block is guaranteed to execute (to clean up resources) unless `System.exit()` is called.

#### Q20. A checked exception in Java is:
- A) Checked by the runtime environment
- B) Checked at compile-time, requiring a `try-catch` block or a `throws` declaration
- C) A type of NullPointerException
- D) Ignored by the compiler
- **Answer: ✅ B**
- **Explanation**: Checked exceptions (e.g., `IOException`) are checked at compile time. The compiler forces the programmer to handle or declare them.

---

## 🔷 Topic 5: Memory Management & Garbage Collection

#### Q21. Stack memory allocation is characterized by:
- A) Manual allocation using `malloc`
- B) Automatic allocation, high speed, and LIFO lifecycle
- C) Susceptibility to external fragmentation
- D) Garbage collection sweeps
- **Answer: ✅ B**
- **Explanation**: Stack allocations are managed by the compiler for local variables. They are fast because the system only adjusts the stack pointer, following LIFO order.

#### Q22. Heap memory allocation is used for:
- A) Storing local function arguments
- B) Return addresses of subroutines
- C) Dynamic memory allocation at runtime
- D) Constant system macros
- **Answer: ✅ C**
- **Explanation**: Heap memory is used when the size or lifetime of data cannot be determined at compile time (e.g., creating objects dynamically with `new`).

#### Q23. In C++, allocating memory with `new` but failing to deallocate it with `delete` leads to:
- A) Segmentation Fault
- B) Memory Leak
- C) Stack Overflow
- D) Dangling Pointer
- **Answer: ✅ B**
- **Explanation**: If memory is allocated on the heap and not released, it remains reserved and unusable, draining system RAM.

#### Q24. In C++, what happens when a base class pointer deletes a derived class object, but the base class destructor is NOT declared as `virtual`?
- A) Compiler Error
- B) Only the base class destructor is called, causing memory leaks in the derived class
- C) Only the derived class destructor is called
- D) Both destructors are called in the correct order
- **Answer: ✅ B**
- **Explanation**: Without a `virtual` destructor in the base class, the compiler binds the destructor call statically to the pointer type (`Base*`), bypassing the derived class destructor.

#### Q25. The JVM Garbage Collector identifies dead objects using which primary criteria?
- A) If the object has been in memory for over 10 minutes
- B) If the object is no longer reachable from any GC Roots
- C) If the object has large memory footprints
- D) If the object is primitive
- **Answer: ✅ B**
- **Explanation**: Reachability analysis determines if an object can be accessed starting from active references (stack variables, static references). Unreachable objects are marked for collection.

---

## 🔷 Topic 6: Conceptual Review Questions

#### Q26. C is considered what type of language?
- A) Object-Oriented
- B) Procedural / Imperative
- C) Functional
- D) Logic
- **Answer: ✅ B**
- **Explanation**: C focuses on step-by-step procedures and function calls rather than objects.

#### Q27. Java source code is compiled into:
- A) Native machine code binaries
- B) Assembly code
- C) Bytecode (stored in `.class` files)
- D) HTML text
- **Answer: ✅ C**
- **Explanation**: The Java compiler (`javac`) compiles source files into intermediate bytecode, which is run by the JVM on any platform.

#### Q28. A pointer that has been deallocated (freed) but still points to its old memory address is called:
- A) Null Pointer
- B) Void Pointer
- C) Dangling Pointer
- D) Wild Pointer
- **Answer: ✅ C**
- **Explanation**: A dangling pointer points to freed memory. Accessing it causes unpredictable behavior or segmentation faults.

#### Q29. Pointer arithmetic (e.g., `ptr + 1`) increments the address stored in the pointer by:
- A) 1 byte
- B) 1 bit
- C) The size of the data type the pointer points to
- D) 4 bytes
- **Answer: ✅ C**
- **Explanation**: The address increments by `sizeof(type)`. For an `int*` on a 4-byte system, `ptr + 1` increases the address by 4.

#### Q30. Which C++ keyword is used to ensure a base class method must be overridden in subclasses, preventing direct instantiation of the base class?
- A) `const`
- B) `static`
- C) `= 0` (Pure Virtual declaration)
- D) `inline`
- **Answer: ✅ C**
- **Explanation**: Specifying `= 0` on a virtual function makes it pure virtual, turning the class into an abstract class.

#### Q31. In Java, what is the default parent class of all classes?
- A) `Main`
- B) `String`
- C) `Object`
- D) `System`
- **Answer: ✅ C**
- **Explanation**: Every class in Java implicitly extends `java.lang.Object`.

#### Q32. Can static methods be overridden in Java?
- A) Yes, always
- B) No, they can only be hidden (Method Hiding)
- C) Only if declared virtual
- D) Only if public
- **Answer: ✅ B**
- **Explanation**: Overriding relies on runtime dynamic dispatch for instance methods. Because static methods belong to the class rather than an instance, they are bound statically at compile time.

#### Q33. Which parameter passing technique is most efficient for passing large structures/classes in C++?
- A) Pass by Value
- B) Pass by Constant Reference (`const Type&`)
- C) Pass by pointer in register
- D) All have identical performance
- **Answer: ✅ B**
- **Explanation**: Pass by reference passes only a pointer-sized address, avoiding copying the large object. Using `const` prevents the function from modifying the original object.

#### Q34. What is the scope of an `extern` variable?
- A) Local to the function it is declared in
- B) File-scope only
- C) Global across multiple files/modules
- D) Restricted to the heap
- **Answer: ✅ C**
- **Explanation**: `extern` declares a global variable that is defined in another source file or module.

#### Q35. What is the primary drawback of using a Mark-and-Sweep garbage collection algorithm?
- A) It cannot clean heap objects
- B) It causes "Stop-the-World" pauses, halting program execution to scan memory
- C) It requires manual destructors
- D) It causes memory leaks
- **Answer: ✅ B**
- **Explanation**: To identify reachable objects safely, GC algorithms must temporarily freeze user thread execution, causing execution pauses.

#### Q36. What is the difference between `delete` and `delete[]` in C++?
- A) `delete` is for objects, `delete[]` is for primitive arrays
- B) `delete` calls the destructor of a single object, while `delete[]` calls the destructors for all elements in an allocated array
- C) `delete[]` is used in Java
- D) There is no difference
- **Answer: ✅ B**
- **Explanation**: Allocating an array with `new Type[N]` requires using `delete[]` to ensure the destructor is called for all $N$ elements in the array.

#### Q37. What is the output of the expression `sizeof` on an array of 5 integers in C++ (assuming a 4-byte integer size)?
- A) 5 bytes
- B) 20 bytes
- C) 40 bytes
- D) 10 bytes
- **Answer: ✅ B**
- **Explanation**: `sizeof(array)` returns the total bytes occupied: $5 \text{ elements} \times 4 \text{ bytes/element} = 20 \text{ bytes}$.

#### Q38. In C++, static member functions can access:
- A) Only static member variables and static functions of the class
- B) Both static and non-static member variables
- C) The `this` pointer
- D) Private instance variables
- **Answer: ✅ A**
- **Explanation**: Static functions belong to the class, not an object. Because they run without a `this` pointer instance context, they cannot access non-static instance variables.

#### Q39. What is a memory leak?
- A) Unchecked file reads
- B) RAM memory space that was dynamically allocated but is no longer reachable by the program, preventing it from being reused
- C) Stack overflow crash
- D) Hardware capacitor failure
- **Answer: ✅ B**
- **Explanation**: Memory leaks occur when heap memory is allocated but references to it are lost before it is freed.

#### Q40. Which keyword in Java prevents a class from being inherited?
- A) `static`
- B) `final`
- C) `const`
- D) `abstract`
- **Answer: ✅ B**
- **Explanation**: Marking a class as `final` prevents it from being extended. Marking a method as `final` prevents it from being overridden.

#### Q41. In C++, a destructor is:
- A) Used to allocate memory
- B) A special member function called automatically when an object goes out of scope to release resources
- C) A runtime error handler
- D) The main compiler thread
- **Answer: ✅ B**
- **Explanation**: Destructors clean up resources (e.g. closing files, releasing memory) when an object is destroyed.

#### Q42. In Java, what happens to memory allocation if `System.gc()` is called?
- A) Immediate guaranteed sweep of the heap
- B) Suggests that the JVM run the Garbage Collector, but does not guarantee execution
- C) The JVM exits
- D) Stack is emptied
- **Answer: ✅ B**
- **Explanation**: `System.gc()` suggests that the JVM run the garbage collector, but the JVM can choose to ignore the call.

#### Q43. What does "Write Once, Run Anywhere" (WORA) refer to?
- A) Standard compiled binary files
- B) Platform independence in Java via Bytecode execution on the JVM
- C) C++ template functions
- D) SQL transactions
- **Answer: ✅ B**
- **Explanation**: Java source code compiles to bytecode, which can run on any device that has a compatible Java Virtual Machine (JVM).

#### Q44. In C++, can you overload the scope resolution operator (`::`)?
- A) Yes, always
- B) No, the scope resolution operator (`::`) is one of the operators that cannot be overloaded
- C) Only inside classes
- D) Only in templates
- **Answer: ✅ B**
- **Explanation**: C++ forbids overloading of: `::` (Scope Resolution), `.` (Member Access), `.*` (Pointer-to-Member), and `?:` (Ternary).

#### Q45. Which of the following refers to early binding?
- A) Static Binding, resolved at compile-time
- B) Dynamic Binding, resolved at runtime
- C) Virtual method lookup
- D) Garbage Collection
- **Answer: ✅ A**
- **Explanation**: Early (static) binding maps method calls to their definitions at compile time.

#### Q46. What is a wild pointer?
- A) A pointer pointing to the first index of an array
- B) An uninitialized pointer pointing to an arbitrary memory location
- C) A double pointer
- D) A pointer that points to a function
- **Answer: ✅ B**
- **Explanation**: A wild pointer is uninitialized. It contains garbage data and points to an arbitrary memory location, which can cause crashes if dereferenced.

#### Q47. If a class in Java implements multiple interfaces, how are duplicate default method signatures resolved?
- A) The program crashes during compilation
- B) The class must override the duplicate method to resolve the ambiguity
- C) The first interface listed takes priority
- D) It is ignored
- **Answer: ✅ B**
- **Explanation**: If a class implements two interfaces containing duplicate default method signatures, the compiler throws an error. The class must resolve the ambiguity by overriding the method.

#### Q48. In C++, pointer arithmetic on a pointer of type `void*` is:
- A) Allowed and increments by 1 byte
- B) Disallowed because the compiler does not know the size of the pointed-to type
- C) Allowed and increments by 4 bytes
- D) Handled dynamically
- **Answer: ✅ B**
- **Explanation**: A `void*` pointer represents an untyped memory address. Because its size is undefined, pointer arithmetic cannot be performed on it.

#### Q49. Which modifier in Java makes a class member accessible only within the same package and by subclasses?
- A) `private`
- B) `protected`
- C) `public`
- D) default (package-private)
- **Answer: ✅ B**
- **Explanation**: In Java, `protected` members are accessible within the same package and by subclasses in other packages.

#### Q50. In C++, the `this` pointer:
- A) Points to the base class
- B) Points to the current object instance inside non-static member functions
- C) Is a static global pointer
- D) Is used to delete objects
- **Answer: ✅ B**
- **Explanation**: The `this` pointer is an implicit parameter passed to all non-static member functions, pointing to the calling object instance.
