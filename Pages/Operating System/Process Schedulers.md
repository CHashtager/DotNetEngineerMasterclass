# Process Schedulers

Process schedulers are components of the operating system that decide which process to run at any given time, based on criteria such as priority, process state, and system load. There are three main types of schedulers:

1. **Short-Term Scheduler (CPU Scheduler)**:
    - **Function**: Selects which process in the ready queue should be executed next by the CPU.
    - **Frequency of Execution**: Operates very frequently (milliseconds) to ensure the CPU remains busy.
    - **Criteria**: Often uses criteria like process priority, shortest job next, or round-robin scheduling.
2. **Medium-Term Scheduler**:
    - **Function**: Temporarily removes processes from main memory and stores them on disk (swapping) when there is a need to free up memory. It can later bring these processes back into memory.
    - **Purpose**: Helps in controlling the degree of multiprogramming and managing memory more efficiently.
3. **Long-Term Scheduler (Job Scheduler)**:
    - **Function**: Determines which processes are admitted from the job queue into the ready queue in main memory, starting the execution process.
    - **Frequency of Execution**: Operates less frequently than the short-term scheduler, as it deals with the admission of new processes into the system.
    - **Criteria**: May consider factors like job priorities, memory requirements, or the need to balance CPU-bound and I/O-bound processes.

## Summary

- **Short-Term Scheduler (CPU Scheduler):** Selects a process from the ready queue and allocates the CPU to it.
- **Medium-Term Scheduler:** Swaps processes between main memory and secondary storage (e.g., disk) to manage memory usage.
- **Long-Term Scheduler (Job Scheduler):** Selects processes from the job queue and loads them into memory for execution.
