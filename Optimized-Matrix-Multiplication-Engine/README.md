# Optimized Matrix Multiplication Engine

## Problem

Process multiple matrix-multiplication requests efficiently by parallelizing work across a custom thread pool instead of doing each matrix pair in a single serial loop.

## What I Implemented

- Batched request pipeline (`t` matrix pairs in one input stream).
- Frontend thread receives a request, transposes matrix `B`, and partitions output cells into work items.
- Backend worker threads that consume work items and compute assigned output ranges.
- Two synchronized queues (request queue and work queue) using `pthread_mutex_t` + `pthread_cond_t`.
- Completion tracking with `works_left` and a condition variable barrier (`tpool_synchronize`).

## Input/Output Format Example

```text
Input
2 2 1
1 2
3 4
5 6
7 8
2

Output
--start--
19 22
43 50
```

## Skills Demonstrated

- Producer-consumer concurrency design with condition variables
- Work decomposition and load partitioning for CPU-bound tasks
- Memory-safe dynamic matrix allocation and cleanup
- Performance-aware data layout transformation (matrix transpose)
