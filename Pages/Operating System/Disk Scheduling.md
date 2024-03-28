# Disk Scheduling

Disk scheduling algorithms are strategies used by operating systems to decide the order in which disk I/O requests are processed. These algorithms aim to optimize the performance of the disk subsystem by reducing seek time (the time it takes for the disk's read/write head to move to the location of the requested data) and minimizing latency.

- **First Come First Served (FCFS):** Requests are served in the order they arrive.
- **Shortest Seek Time First (SSTF):** The request with the minimum seek time from the current head position is served next.
- **Scan:** The disk arm moves back and forth across the disk, servicing requests in the direction of its movement.
- **C-Scan:** Similar to Scan, but the disk arm moves in only one direction and resets to the other end after servicing requests.
- **Look:** Similar to Scan, but the disk arm only goes as far as the last pending request in each direction.
- **C-Look:** Similar to C-Scan, but the disk arm only goes as far as the last pending request in the current direction.

## **First Come First Served (FCFS)**

- **Description**: This is the simplest disk scheduling algorithm. Requests are processed in the exact order they arrive in the queue.
- **Pros**: Fairness, as no request is prioritized over another.
- **Cons**: Not efficient in terms of overall system performance, especially when requests are scattered across the disk.

## **Shortest Seek Time First (SSTF)**

- **Description**: Chooses the request that is closest to the current head position, thereby minimizing the seek time for the next request.
- **Pros**: Reduces the average seek time compared to FCFS.
- **Cons**: Can lead to starvation, where requests frequently far from the head may wait a very long time to be serviced.

## **Scan (Elevator Algorithm)**

- **Description**: The disk arm starts at one end of the disk and moves toward the other end, servicing requests along the way. Upon reaching the other end, the direction is reversed, and the process continues in a back-and-forth manner.
- **Pros**: Offers a more uniform wait time compared to SSTF.
- **Cons**: Requests just missed by the arm have to wait for the arm to traverse the entire disk and come back.

## **C-Scan (Circular Scan)**

- **Description**: Similar to Scan, but instead of reversing direction, the arm goes back to the starting end of the disk after reaching the other end and continues processing requests.
- **Pros**: Provides a more uniform wait time for requests across the disk.
- **Cons**: Requests at the beginning of the disk may experience longer wait times after the arm resets.

## **Look**

- **Description**: A variation of the Scan algorithm where the arm only goes as far as the last request in each direction before reversing or stopping, rather than traveling to the end of the disk.
- **Pros**: Reduces unnecessary movement of the disk arm, leading to improved efficiency.
- **Cons**: Like Scan, requests just missed can experience longer wait times.

## **C-Look (Circular Look)**

- **Description**: Similar to C-Scan, but the arm only goes as far as the last request in the direction of movement. After servicing the last request, it immediately jumps back to the first request in the opposite direction without servicing any requests on the return trip.
- **Pros**: Reduces the traversal time of the disk arm, potentially decreasing the average wait time.
- **Cons**: Requests at one end of the disk might wait longer if the arm frequently doesn't reach that end before jumping back.
