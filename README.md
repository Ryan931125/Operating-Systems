# Operating Systems Projects (C)

This repository collects my projects from the Operating Systems course. Each project focuses on a different systems topic: network services, process trees with IPC, user-space threading, and parallel compute pipelines.

## What This Repository Demonstrates

- System-level C programming on Unix-like platforms
- Process and thread orchestration using `fork`, `exec`, `pipe`, `pthread`, `setjmp` and `longjmp`
- Synchronization and race-condition control (`fcntl` record locking and read/write lock coordination)
- Work partitioning, scheduling, and queue-based task execution
- Robust command parsing and stateful runtime behavior

## Project Index

### [Concurrent TCP Server Multiplexing](./Concurrent-Tcp-Server-Multiplexing)

Train-seat booking service with separate read/write server modes, stateful booking flow, and seat-level file locking to protect shared records.

### [Multi-Process Tree IPC](./Multi-Process-Tree-Ipc)

Hierarchical process tree where each node is a process communicating via pipes to support recursive commands (`Meet`, `Check`, `Graduate`).

### [User-Space Threading Runtime](./User-Space-Threading-Runtime)

Custom user-level threading runtime with context switching, signal-driven scheduling, sleep/wakeup, waiting queues, and read/write lock semantics.

### [Optimized Matrix Multiplication Engine](./Optimized-Matrix-Multiplication-Engine)

Producer-consumer style thread pool for batched matrix multiplication using request decomposition and backend worker execution.