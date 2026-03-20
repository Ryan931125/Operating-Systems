# Concurrent TCP Train Booking Server

## Problem

Design a TCP service for train-seat reservation with two roles:

- `READ_SERVER`: query seat maps for a shift.
- `WRITE_SERVER`: select seats and commit payment.

The key OS challenge is consistency when multiple clients target the same seat record.

## What I Implemented

- Two compile-time server modes (`-D READ_SERVER` and `-D WRITE_SERVER`) with shared core logic.
- Stateful write flow: `SHIFT -> SEAT -> BOOKED`.
- Per-seat advisory file locking using `fcntl` record locks (byte-range lock per seat slot).
- Seat toggle behavior in write mode (choose/cancel before payment).
- Commit logic that updates persistent seat files and releases acquired locks.
- Graceful client-exit handling with lock cleanup.

## Example Interaction

```text
======================================
 Welcome to CSIE Train Booking System
======================================
Please select the shift you want to book [902001-902005]: 902001

Booking info
|- Shift ID: 902001
|- Chose seat(s):
|- Paid:

Select the seat [1-40] or type "pay" to confirm: 12
Select the seat [1-40] or type "pay" to confirm: pay
>>> Your train booking is successful.
Type "seat" to continue or "exit" to quit [seat/exit]: exit
>>> Client exit.
```

## Skills Demonstrated

- TCP socket lifecycle (`socket`, `bind`, `listen`, `accept`, `read`, `write`)
- Persistent shared-state coordination through file descriptors and region locks
- Protocol/state-machine implementation for interactive network services
- Failure-path handling and cleanup in long-running server processes

## Scope Note

This codebase primarily demonstrates booking-state logic and lock-safe updates. The assignment context references I/O multiplexing, while the current version runs a blocking connection loop.
