Pintos Project: Threads and User Programs

This repository contains a group implementation of Project 1 (Threads) and Project 2 (User Programs) for the Pintos instructional operating system. Pintos is a simple, x86-based operating system framework designed to teach the core concepts of OS kernels.

Project 1: Threads
The primary goal of this phase was to replace the default "busy-waiting" alarm clock with a more efficient block/unblock mechanism and to implement a sophisticated thread scheduler.

Alarm Clock: Re-implemented timer_sleep() using thread blocking to eliminate CPU wastage.
Priority Scheduling: Developed a priority-based scheduler where the highest-priority thread always runs first.
Priority Donation: Implemented donation logic to solve the Priority Inversion problem, allowing threads to temporarily donate priority to locks held by lower-priority threads.

Project 2: User Programs
This phase focused on enabling the kernel to run user-space programs, requiring the implementation of memory protection and system calls.
Argument Passing: Developed a mechanism to parse command-line arguments and set up the user stack for process initialization.

System Calls: Implemented a robust System Call Handler to bridge the gap between user space and kernel space. Supported syscalls include:
Process Control: halt, exit, exec, wait.
File Operation: create, remove, open, filesize, read, write, seek, tell, close.
Memory Protection: Ensured the kernel is protected from malicious or buggy user programs by validating user-provided pointers and memory access.
