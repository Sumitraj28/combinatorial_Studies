# Unit I: Operating Systems - Lab Practicals

This guide contains complete code, detailed walkthroughs, and execution instructions for the first four practical experiments of the CSE357 course.

---

## 💻 Experiment 1: Introduction to Linux Commands

Linux command line is the base of operating system interactions. Below are the key commands organized by their system function:

### 1.1 Directory & File Operations
*   `pwd`: Print Working Directory. Shows your current location.
*   `ls`: Lists files. Common flags:
    *   `ls -l`: Long format (permissions, owner, size, date modified).
    *   `ls -a`: List all files, including hidden ones (prefixed with `.`).
*   `mkdir <dir_name>`: Creates a directory.
*   `cd <path>`: Change directory. `cd ..` moves up one folder.
*   `touch <file_name>`: Creates an empty file.
*   `cp <source> <dest>`: Copies files or directories (use `-r` for recursive copy).
*   `mv <source> <dest>`: Moves or renames files.
*   `rm <file_name>`: Deletes a file. Use `rm -rf` to recursively force delete directories.

### 1.2 File Permissions & Ownership
In Linux, every file has three permission groups: **User/Owner (u)**, **Group (g)**, and **Others (o)**.
Permissions can be represented numerically: **Read (4)**, **Write (2)**, and **Execute (1)**.

```bash
# Set permissions: Read/Write/Execute for Owner, Read/Execute for Group, Read only for Others
# 7 = 4+2+1 (rwx), 5 = 4+0+1 (r-x), 4 = 4+0+0 (r--)
chmod 755 script.sh

# Change file owner
chown root file.txt
```

### 1.3 Process Management
*   `ps`: Reports a snapshot of the current processes. Use `ps aux` for all system processes.
*   `top`: Displays real-time CPU/memory utilization and process execution.
*   `kill <PID>`: Terminate a process by its Process ID. Use `kill -9` to force terminate.

### 1.4 Searching & Filtering
*   `grep "<pattern>" <file>`: Searches for a string or regex pattern in a file.
*   `find <path> -name "<filename>"`: Locates files within a directory hierarchy.

---

## 💻 Experiment 2: Shell Programming (Bash Scripting)

A shell script is a file containing a sequence of commands executed by the shell interpreter.

### Task: Bash Script to Generate Fibonacci Series up to N terms
Create a file named `fibonacci.sh` and add the following script:

```bash
#!/bin/bash
# The first line (shebang) tells the system to use the Bash interpreter.

echo -n "Enter the number of terms: "
read n

# Initialize the first two terms
a=0
b=1

echo "The Fibonacci Series is: "

for (( i=0; i<n; i++ ))
do
    echo -n "$a "
    # Calculate next term
    fn=$((a + b))
    # Update terms
    a=$b
    b=$fn
done
echo "" # Prints a final newline
```

### How to Run:
1.  Save the code as `fibonacci.sh`.
2.  Make the script executable:
    ```bash
    chmod +x fibonacci.sh
    ```
3.  Run the script:
    ```bash
    ./fibonacci.sh
    ```

---

## 💻 Experiment 3: System Calls in C (Process & File Operations)

System calls allow C programs to ask the kernel to perform operations (like creating processes or writing files) on their behalf.

### Task: Spawning a Child Process using `fork()` and managing execution via `wait()`
This C program creates a child process. The child process prints its PID and exits, while the parent process waits for the child to finish before exiting.

```c
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <sys/types.h>
#include <sys/wait.h>

int main() {
    pid_t pid;

    printf("Prior to fork: My PID is %d\n", getpid());

    // Spawn a child process
    pid = fork();

    if (pid < 0) {
        // fork failed
        perror("Fork failed");
        exit(EXIT_FAILURE);
    } 
    else if (pid == 0) {
        // Child execution path
        printf("Hello from Child! Child PID: %d, Parent PID: %d\n", getpid(), getppid());
        sleep(2); // Simulate task
        printf("Child process is exiting...\n");
        exit(0);
    } 
    else {
        // Parent execution path
        printf("Hello from Parent! Parent PID: %d, Child PID: %d\n", getpid(), pid);
        printf("Parent is waiting for child to finish...\n");
        
        // Wait for child process to terminate
        wait(NULL);
        
        printf("Child has finished. Parent is now exiting.\n");
    }

    return 0;
}
```

### How to Compile & Run:
```bash
# Compile using GCC compiler
gcc process_syscall.c -o process_syscall

# Run the executable
./process_syscall
```

---

## 💻 Experiment 4: Multithreading using Pthread Library

A thread is a single sequence stream within a process. Multiple threads share code, heap data, and system resources, but execute concurrently.

### Task: Creating and Joining Threads in C
This program creates two parallel threads. Thread 1 prints odd numbers up to 10, and Thread 2 prints even numbers up to 10. They use a shared lock (Mutex) to prevent printing outputs from scrambling together.

```c
#include <stdio.h>
#include <stdlib.h>
#include <pthread.h>
#include <unistd.h>

// Shared Mutex lock
pthread_mutex_t lock;

void* print_odds(void* arg) {
    for (int i = 1; i <= 10; i += 2) {
        pthread_mutex_lock(&lock);
        printf("Thread 1 (Odds): %d\n", i);
        pthread_mutex_unlock(&lock);
        usleep(50000); // sleep for 50ms
    }
    return NULL;
}

void* print_evens(void* arg) {
    for (int i = 2; i <= 10; i += 2) {
        pthread_mutex_lock(&lock);
        printf("Thread 2 (Evens): %d\n", i);
        pthread_mutex_unlock(&lock);
        usleep(50000); // sleep for 50ms
    }
    return NULL;
}

int main() {
    pthread_t thread1, thread2;

    // Initialize the mutex
    if (pthread_mutex_init(&lock, NULL) != 0) {
        printf("Mutex initialization failed\n");
        return 1;
    }

    printf("Starting threads...\n");

    // Create Thread 1 (Odds)
    if (pthread_create(&thread1, NULL, print_odds, NULL) != 0) {
        perror("Failed to create thread 1");
        return 1;
    }

    // Create Thread 2 (Evens)
    if (pthread_create(&thread2, NULL, print_evens, NULL) != 0) {
        perror("Failed to create thread 2");
        return 1;
    }

    // Wait (join) for both threads to finish execution
    pthread_join(thread1, NULL);
    pthread_join(thread2, NULL);

    // Destroy mutex
    pthread_mutex_destroy(&lock);

    printf("Both threads finished execution. Main exiting.\n");
    return 0;
}
```

### How to Compile & Run:
> [!IMPORTANT]
> You must link the Posix Threads library when compiling using the `-lpthread` flag.

```bash
# Compile linking the thread library
gcc pthreads_demo.c -o pthreads_demo -lpthread

# Run the executable
./pthreads_demo
```
