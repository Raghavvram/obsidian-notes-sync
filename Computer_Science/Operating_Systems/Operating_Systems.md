
## Disk Management
###### What are the differences between Basic and Dynamic Disks?
Basic disks use traditional partitions, while dynamic disks offer advanced features like spanning and mirroring.

###### What is the purpose of a Boot Block?
It stores the full bootstrap program required to start the operating system.

###### What is disk partitioning?
It is the physical division of a disk drive into one or more regions.

###### What is a Cylinder?
A cylinder is **a division of data in a disk drive**

###### What is the difference between a Volume and a Partition?
A partition is a physical division of a disk, while a volume is a logical division of a disk.

###### What is Low-Level Formatting?
It divides a disk into sectors so the disk controller can read and write data.

###### What is Sector Sparing?


###### What is Seek Time?
The time it takes for the disk arm to move to the correct track.

###### What is Rotational Latency?
The time it takes for the desired sector to rotate under the read/write head.

###### What is Transfer Time?

###### What is Disk Response Time?
The total time to service a disk request: seek time + rotational latency + transfer time.

###### What are some disk scheduling algorithms?
FCFS, SSTF, SCAN, C-SCAN, LOOK, and C-LOOK are common disk scheduling algorithms.

###### What is Stable Storage?
A classification of storage that survives any single-point failure.

###### What is the difference between data striping and data mirroring?
Striping distributes data across disks for performance; mirroring duplicates data for redundancy.

###### What is a hot spare in RAID?
A standby disk that automatically replaces a failed disk in a RAID array.

###### What is degraded mode in RAID?
When a RAID array continues to operate with a failed disk, often with reduced performance.

###### How is data reconstructed in RAID after a disk failure?
Data is rebuilt using parity information or from a mirrored copy on other disks in the array.

###### What is the "write hole" in RAID 5?
A data inconsistency that can occur if a power failure happens during a stripe write.

###### What is a stripe set?
A set of disks that have their data interleaved in a RAID configuration.

###### What is RAID?
Redundant Array of Independent Disks, a way to store data on multiple hard disks.

###### What is a file allocation table (FAT)?
A table that an operating system maintains on a hard disk that provides a map of the cluster.

## I/O Management
###### What are the key registers in an I/O port?
Typically data, status, and control registers.

###### How does the CPU interact with I/O devices?
Through memory-mapped I/O (MMIO) or port-mapped I/O (PMIO).

###### What is I/O Polling?
The CPU repeatedly checks an I/O device's status to see if it is ready for data transfer.

###### What is an interrupt?
A signal to the CPU from hardware or software indicating an event that needs immediate attention.

###### What is interrupt-initiated I/O?
An I/O method where the device signals the CPU when it's ready, avoiding polling.

###### What is interrupt nesting?
A higher-priority interrupt can preempt the execution of a lower-priority interrupt handler.

###### What is Direct Memory Access (DMA)?
It allows I/O devices to transfer data directly to/from main memory, bypassing the CPU.

###### What is an I/O Control Block (IOCB)?
A data structure in the OS kernel that represents an I/O request.

###### What is double buffering?
Using two buffers for I/O to allow one to be filled while the other is being emptied.

###### What is a device driver?
Software that allows the operating system to communicate with a hardware device.

## File Management

## Security Management