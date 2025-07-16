Disk Management
IO Management
File Management
Security Management

###### What are Basic and Dynamic Disks ?

Basic disks: traditional partitioning schemes. creating primary and extended partitions.

Dynamic disks: Offers more advance features like spanning, mirroring, stripped.

###### What is the use of Boot Block ?

the full bootstrap programs is stored in partition called boot block

###### What is partitioning ?

Physical Division

###### What is a Cylinder

###### Diff bet Volume and Partition ?

Partition - Physical Division into tracks
Volume - Logical Devision

###### What is Low-Level Formatting ?

Before a disk can store data, it must be divided into sectors that the disk can read and write.

###### What is Sector Sparing ?

###### What is seek Time ?

Time taken for the disk arm to move to the correct track

###### What is Rotational Latency ?

The time taken for the desired sector to rotate under the read/write head

###### What is Transfer Time ?

###### What is Response Time ?

(seek time + rot lat + transfer time)

###### Disk Scheduling Algorithm

###### Stable Storage / Tertiary Storage

###### What is data striping and data mirroring ?

Striping distributes data across multiple disk for inc. performance, while mirroring creates duplicate across multiple disk

###### What is hot spare in RAID ?

###### What is degraded mode of operation in RAID ?

Depending on the RAID level, the OS rebuilds the data from parity information or from the mirrored copy on another disk.

###### How is data reconstructed after a disk failure in RAID ?

###### What is a write Hole in RAID 5?

###### What is a stripe set ?

A group of disks that are used to store together

#### I/O

###### What are the key registers in an IO port ?

###### How does the CPU interact with I/O devices ?

Memory Mapped(accessing ports as memory locations) or Port Mapped(special instruction)

###### what is Polling ?

technique where the CPU repeatedly checks the status of an I/O device to see if its ready for data transfer.

###### What is a interrupt ?

disturbance in normal flow

###### What is a interrupt-initiated ?

Allows device to signal the CPU when its read for data transfer, rather than the CPU constantly checking.

###### What is a interrupt nesting?

higher priority interrupts to interrupts the processing of lower-interrupts.

###### What is DMA ?

allows drivers to transfer data directly to and from memory without CPU intervention, improving efficiency

###### What are IO Control Block
