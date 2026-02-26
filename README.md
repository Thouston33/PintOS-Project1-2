[PintOS_README (1).md](https://github.com/user-attachments/files/25563291/PintOS_README.1.md)
# PintOS — Operating System Kernel

An implementation of core operating system components built on top of the PintOS educational kernel framework in C. Completed across two projects covering thread scheduling and user program execution.

> Developed in partnership as part of CSE 421 (Operating Systems) at the University at Buffalo.

---

## Project 1 — Threads

Extended the PintOS kernel with a fully functional thread scheduling system.

### Implemented
- **Alarm Clock** — Replaced the busy-wait `timer_sleep()` implementation with a sleep queue that blocks threads and wakes them at the correct tick, eliminating CPU spinning
- **Priority Scheduling** — Overhauled the thread scheduler to always run the highest-priority ready thread, including preemption on thread creation and unblocking
- **Priority Donation** — Implemented priority inheritance to resolve priority inversion, handling nested donation chains and multiple simultaneous donations through lock acquisition

---

## Project 2 — User Programs

Extended the kernel to load and execute user-level programs, bridging the gap between user space and kernel space.

### Implemented
- **Argument Passing** — Tokenized command-line strings and set up the user stack in accordance with the x86 calling convention, pushing arguments, pointers, and the stack sentinel in the correct order
- **System Calls** — Implemented the system call handler and a full suite of syscalls including `halt`, `exit`, `exec`, `wait`, `read`, `write`, `create`, `remove`, `open`, `close`, and `filesize`
- **User Memory Validation** — Added robust pointer validation before every kernel memory access to safely reject bad or null pointers from user programs without crashing the kernel
- **Process Synchronization** — Used semaphores to coordinate parent-child process relationships for `exec` and `wait`, ensuring correct exit code passing between processes

### Stack Setup
A key implementation highlight in Project 2 was correctly constructing the initial user stack before jumping to `main()`. This involved:
1. Pushing argument strings onto the stack in reverse order
2. Word-aligning the stack pointer to a 4-byte boundary
3. Pushing null sentinel, then argument pointers (`argv[]`) in reverse
4. Pushing `argv`, `argc`, and a fake return address

Getting this right required careful pointer arithmetic and close adherence to the x86 System V ABI — any misalignment or ordering mistake would silently corrupt program startup.

---

## Tech Stack

- **Language** — C
- **Architecture** — x86 (32-bit)
- **Framework** — PintOS educational OS kernel
- **Tools** — GCC, GDB, QEMU

---

## Notes

This repository contains Projects 1 and 2 only. Projects 3 (Virtual Memory) and 4 (File Systems) are not included.
