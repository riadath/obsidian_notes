# Monoprogramming

![[Pasted image 20231127155528.png|600x300]]

- Works when there's only one process running or only one thing to do
- Memory available = Memory required
- Poor CPU utilization when I/O present (too much wait time)
- Poor memory utilization with a varied job mix


# Multiprogramming / Multitasking

- Subdivide memory for running more than one task
## Fixed Partitioning

### Fixed Equal Sized Partitioning
##### **How?**
- Divide into fixed equal sized partitions
- any process requiring <= partition size can be loaded into any partition
##### **Problem?**
- Unused space wasted (Internal fragmentation)
- Processes larges then the partition cannot run
### Fixed Variable Sized Partitioning

![[Pasted image 20231127161113.png]]

- Place a process in the queue for the smallest partition that it fits in

#### **Problem?**
