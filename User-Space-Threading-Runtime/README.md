# User-Space Threading Runtime

## Problem

Build a user-level threading system in C that schedules and synchronizes logical threads inside one process, without relying on kernel thread APIs for context switching behavior.

## What I Implemented

- Thread Control Block (`struct tcb`) with per-thread execution state.
- Context save/restore with `setjmp` and `longjmp`.
- Scheduler with ready queue, waiting queue for lock contention, and sleeping set for timed suspension.
- Signal-driven preemption hooks (`SIGALRM`, `SIGTSTP`) with a central scheduler jump buffer.
- Read/write lock semantics (`read_lock`, `write_lock`, unlock operations).
- Thread operations via macros: create/setup/yield/sleep/awake/exit.
- Demonstration routines: `fibonacci`, `pm` (alternating-sign progression), and `enroll` (locking + scheduling behavior under shared class-capacity state).

## Example Output Snippet

```text
thread 1: set up routine fibonacci
thread 2: set up routine pm
thread 1: F_1 = 1
thread 2: pm(1) = 1
caught SIGALRM
thread 1: F_2 = 1
thread 2: pm(2) = -1
```

## Skills Demonstrated

- Cooperative and signal-assisted scheduling in user space
- Queue-based runtime design and explicit thread-state transitions
- Synchronization primitives for shared-state safety
- Debugging timing and ordering behavior in concurrent runtimes
