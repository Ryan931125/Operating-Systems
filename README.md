# Systems Programming in UNIX Environments

This repository contains a collection of core systems programming projects focusing on operating system principles, low-level UNIX environments, and concurrent application design.

These projects explore the internals of process management, inter-process communication (IPC), multithreading, network programming, and workload optimization. All implementations are written in C/C++.

## 🛠️ Core Skills & Concepts Learned

* **Network Programming & Concurrency:** Implemented a multi-user network server using I/O multiplexing (`select`/`poll`) to handle concurrent client requests without blocking.
* **Process Management & IPC:** Designed robust multi-process architectures using `fork()`, `exec()`, and `pipe()` for complex communication pipelines.
* **Low-Level Threading & Scheduling:** Built a user space threading runtime from scratch, including custom context switching (`setjmp`/`longjmp`) and thread scheduling.
* **Synchronization & Safety:** Applied mutexes, semaphores, and file locking (`flock()`) to prevent race conditions and ensure data consistency across shared resources.
* **Performance Optimization:** Optimized system workloads with parallelism and efficient memory access patterns.

---

## 📂 Project Overview

### 1. [Concurrent TCP Server with Multiplexing](./Concurrent-Tcp-Server-Multiplexing)

A robust multi-user network server simulating a train seat reservation system.

* Handled concurrent client connections utilizing I/O multiplexing instead of multi-threading.
* Implemented strict file locking mechanisms to guarantee record consistency during simultaneous read/write operations.
* Managed connection timeouts and unexpected client disruptions gracefully via custom signal handling.

### 2. [Multi-Process Tree with IPC](./Multi-Process-Tree-Ipc)

A dynamic process tree modeling real-world social connections and hierarchical data.

* Orchestrated complex parent-child process relationships using `fork()` and `exec()`.
* Designed custom Inter-Process Communication (IPC) pipelines using `pipe()` and file descriptor duplication (`dup()`) to route queries and commands throughout the tree.
* Handled safe process termination and resource cleanup to prevent zombie processes.

### 3. [User-Space Threading Runtime](./User-Space-Threading-Runtime)

A custom user-level thread library enabling cooperative multitasking within a single process.

* Designed a Thread Control Block (TCB) to track thread states, metadata, and stack pointers.
* Implemented custom context switching leveraging `setjmp()` and `longjmp()` to bypass kernel-level threading overhead.
* Built synchronization primitives (mutexes/semaphores) and a custom scheduler to manage thread execution order safely.

### 4. [Optimized Matrix Multiplication Engine](./Optimized-Matrix-Multiplication-Engine)

A high-performance calculation engine focused on optimizing workloads with parallelism.

* Implemented efficient matrix multiplication algorithms tailored to specific matrix constraints.
* Focused on memory-safe data parsing and handling edge cases for incompatible data structures.
