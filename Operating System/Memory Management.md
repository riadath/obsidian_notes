# <u>Monoprogramming</u>

![[Pasted image 20231127155528.png|600x300]]

- Works when there's only one process running or only one thing to do
- Memory available = Memory required
- Poor CPU utilization when I/O present (too much wait time)
- Poor memory utilization with a varied job mix


# <u>Fixed Partitioning for Multitasking</u>

### Fixed Equal Sized Partitioning
##### **How?**
- Divide into fixed equal sized partitions
- any process requiring <= partition size can be loaded into any partition
##### **Problem?**
- Unused space wasted (Internal fragmentation)
- Processes larges then the partition cannot run

Internal Fragmentation :   
Internal fragmentation occurs  when memory allocated to a process contains more space than the process actually needs. 
### Fixed Variable Sized Partitioning

![[Pasted image 20231127161113.png|200x250]]

- Place a process in the queue for the smallest partition that it fits in

#### **Problem?**
- Some partitions may be idle
	- Small processes available but only large partitions are free
**Solution to this problem**:
- A single queue that searches for any process that fits
- Small process in large partitions if necessary
- Increases Internal fragmentation


# Dynamic Partitioning
**External Fragmentation:** 
- Refers to the phenomenon where free memory blocks are scattered throughout the system, but they are not contiguous.
	- Space wasted external to the allocated memory region.
