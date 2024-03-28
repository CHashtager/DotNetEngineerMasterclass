# Concurrent Concepts

- **Kernel:** The core component of an operating system that manages system resources and provides services to user applications.
- **Fork:** A system call used to create a new process, which is an almost identical copy of the calling process.
- **Context Switching:** The process of storing and restoring the state (context) of a process to switch between different processes.
- **User-Level and Kernel-Level Threads:** User-level threads are managed by user-level libraries, while kernel-level threads are managed directly by the operating system kernel.
- **Process vs Thread:** A process is an instance of a program, while a thread is a lightweight unit of execution within a process.
- **Multithreading vs Multiprocessing:** Multithreading allows multiple threads to share resources within a single process, while multiprocessing involves running multiple processes concurrently.
- **Starvation:** A situation where a process or thread is continuously denied access to resources it requires, potentially leading to an indefinite wait.

## **Kernel**

The kernel is the most critical component of an operating system. It acts as a mediator between applications and the computer's hardware. The kernel manages system resources such as CPU, memory, and I/O devices, and it handles system calls, which are requests from user-space applications for services provided by the kernel.

## **Fork**

**`Fork`** is a system call that creates a new process. The new process, referred to as the child process, is a duplicate of the calling process, known as the parent process, except for the returned value. Forking is a common way to perform parallel tasks in Unix-like operating systems.

## **Context Switching**

Context switching is the process of saving the state of a currently running process or thread so that it can be resumed later and activating another process or thread. This is crucial in a multitasking environment to ensure that the CPU can be shared among multiple processes. Context switching involves overhead and can impact system performance if excessive.

## **User-Level and Kernel-Level Threads**

- **User-Level Threads**: These threads are managed without kernel support, typically by a runtime library or user-level process. The kernel is unaware of these threads and sees them as a single process. This approach offers flexibility and efficiency but lacks true concurrency and kernel-level services.
- **Kernel-Level Threads**: Managed directly by the operating system kernel, allowing true parallel execution on multiprocessor systems. The kernel has full knowledge of all threads, enabling better scheduling and management. However, creating and managing kernel threads can be more resource-intensive than user-level threads.

## **Process vs Thread**

- **Process**: A process is an instance of a running program and includes the program code, its current activity, and the resources allocated to it such as memory and file handles. Processes are isolated from each other, providing stability and security.
- **Thread**: A thread is the smallest unit of execution within a process. Threads within the same process share resources like memory and file descriptors, which allows for efficient communication and data exchange but requires synchronization to prevent conflicts.

## **Multithreading vs Multiprocessing**

- **Multithreading**: Involves running multiple threads within a single process. This allows for efficient use of resources and faster execution as threads can share memory and resources directly. However, it requires careful synchronization to avoid issues like race conditions.
- **Multiprocessing**: Refers to running multiple processes concurrently. Processes are fully isolated, which enhances stability and security but at the cost of higher overhead for communication and resource sharing.

## **Starvation**

Starvation occurs when a process or thread is perpetually denied the necessary resources to make progress, often due to scheduling algorithms or resource allocation policies that favor other processes or threads. Starvation can lead to significant performance issues and requires careful management of resources and fair scheduling policies to prevent.
