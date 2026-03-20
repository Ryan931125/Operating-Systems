# Multi-Process Tree IPC

## Problem

Model a dynamic friendship tree where each node is its own Unix process, and tree operations are performed by command propagation through inter-process channels.

## What I Implemented

- Process-per-node tree model with parent-child control channels.
- `Meet parent child_value`: creates a child process via `fork` and `exec`, wires dedicated pipes, and registers the child in the local process table.
- `Check node`: recursively locates a subtree root and prints nodes level-by-level using command fan-out and response aggregation.
- `Graduate node`: recursively terminates a subtree, closes file descriptors, and reaps children (`waitpid`) to avoid zombies.
- Internal coordination commands (`Print`, `Die`) to support tree traversal and controlled shutdown.

## Example Command/Output

```text
Meet Not_Tako Alice_80
Not_Tako has met Alice by himself

Meet Alice Bob_60
Not_Tako has met Bob through Alice

Check Not_Tako
Not_Tako
Alice_80
Bob_60

Graduate Not_Tako
Congratulations! You've finished Not_Tako's annoying tasks!
```

## Skills Demonstrated

- Recursive command routing across process hierarchies
- Low-level IPC with `pipe`, `dup2`, `fdopen`, blocking reads, and full-write loops
- Careful process lifecycle and descriptor cleanup
- Designing protocol-like parent-child acknowledgements (`found`, `no`, `Idie`)

## Scope Note

The assignment includes an `Adopt` operation; this repository version focuses on `Meet`, `Check`, and `Graduate` as the completed core features.
