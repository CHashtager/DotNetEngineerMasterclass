# Memory Management

Memory management is a fundamental aspect of operating systems, ensuring that each process has the necessary memory to execute while maximizing the efficiency and utilization of the system's memory resources.

## Summary

- **Loading Process into Memory:**
  - **Contiguous Allocation:**
    - **Fixed Partitioning:** Memory is divided into fixed-size partitions.
    - **Dynamic Partitioning:** Partitions are allocated dynamically, and compaction is used to reduce external fragmentation.
- **Non-Contiguous Allocation:** Processes are scattered in memory, using techniques like paging or segmentation.
- **Frame:** A fixed-size block of main memory used for memory allocation.
- **Page and Page Table:** Memory is divided into equal-sized pages, and a page table maps virtual addresses to physical addresses.
- **Paging and Multi-Level Paging:** Techniques for mapping virtual addresses to physical addresses using page tables.
- **Virtual Memory:** A technique that allows processes to access more memory than physically available by using secondary storage.
- **Page Hit and Page Fault:** A page hit occurs when the requested page is in memory, while a page fault triggers fetching the page from secondary storage.

### **Loading Process into Memory**

When a process is created or executed, it must be loaded into memory. The operating system handles this by allocating the required memory space to the process, considering the current memory usage and the process's needs.

### **Contiguous Allocation**

Contiguous allocation involves assigning a single continuous block of memory to a process.

- **Fixed Partitioning**: The memory is divided into fixed-size partitions, each of which can hold exactly one process. This method can lead to internal fragmentation if the process's memory requirement is less than the partition size.
- **Dynamic Partitioning**: Memory partitions are created dynamically to fit the size of the requesting process, which helps in reducing wasted space. However, this can lead to external fragmentation over time, and compaction may be needed to consolidate free memory spaces.

### **Non-Contiguous Allocation**

In non-contiguous allocation, a process can occupy multiple non-adjacent areas in memory. This approach reduces fragmentation and allows for more flexible memory utilization.

- **Paging**: Memory is divided into fixed-size blocks called pages, and processes are divided into pages of the same size. A page table is used to map a process's virtual pages to physical frames in memory, allowing for non-contiguous allocation.
- **Segmentation**: Similar to paging, but segments can be of various lengths, representing different logical parts of a program (e.g., code, data, stack). This allows memory to be more closely matched to the process's logical structure.

### **Frame**

A frame is a fixed-size block of main memory, equivalent in size to a page, used as the basic unit of memory allocation in paging systems.

### **Page and Page Table**

- **Page**: A fixed-size block of virtual memory.
- **Page Table**: A data structure used by the operating system to store mappings from virtual addresses to physical frame addresses in memory.

### **Paging and Multi-Level Paging**

- **Paging**: A memory management scheme that eliminates the need for contiguous allocation of physical memory by dividing memory into fixed-sized pages.
- **Multi-Level Paging**: An extension of paging that uses multiple levels of page tables to reduce the memory required to store each process's page table.

### **Virtual Memory**

Virtual memory allows a computer to compensate for physical memory shortages by temporarily transferring data from random access memory (RAM) to disk storage. This process creates the illusion for users of a very large (virtual) memory.

### **Page Hit and Page Fault**

- **Page Hit**: Occurs when the data the process needs to access is already in memory, allowing for immediate access.
- **Page Fault**: Occurs when the data the process needs is not in memory, necessitating reading the data from secondary storage (e.g., hard disk) into memory.
