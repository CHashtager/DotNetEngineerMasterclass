# File System

Lays out the rules for how files are named, stored, and accessed by the OS and applications.

- **File Allocation Table (FAT):** A data structure used in some file systems to track and locate file data on disk.
- **Seek Time:** The time taken for the disk read/write head to move to the desired track.
- **Rotational Latency:** The time taken for the desired sector to rotate under the read/write head.

## **File Allocation Table (FAT)**

The File Allocation Table (FAT) is a classic file system architecture used in many computer systems, notably in early versions of Microsoft Windows and in memory cards and USB flash drives due to its simplicity. FAT maintains a table that acts as a map of the disk's contents. Each entry in the FAT corresponds to a block of the disk, indicating the next block in a file or marking the block as the end of a file. This chaining method allows files to be stored in non-contiguous blocks on the disk, facilitating dynamic file allocation and growth. However, FAT systems can suffer from fragmentation over time, leading to decreased performance.

## **Seek Time**

Seek time refers to the time it takes for the disk's read/write head to move to the correct track on the disk where the desired data is stored. Disk drives contain platters divided into concentric circles called tracks, which are further divided into sectors. When a read or write operation is initiated, the drive must first move the head to the correct track. Seek time is a critical component of disk access time and can significantly affect overall system performance, especially in systems with heavy disk I/O operations. Minimizing seek time is crucial for improving the responsiveness and throughput of storage devices.

## **Rotational Latency**

Rotational latency is the delay waiting for the rotation of the disk to bring the desired sector under the read/write head. Once the head is positioned over the correct track (after the seek time), it must wait for the disk to rotate the correct sector into position. Rotational latency depends on the rotational speed of the disk, measured in revolutions per minute (RPM). Higher RPM values result in lower rotational latency, which contributes to faster read and write operations. Solid-state drives (SSDs) eliminate rotational latency entirely by using non-mechanical storage methods, offering significantly faster data access times.
