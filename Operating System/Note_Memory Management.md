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


# <u>Dynamic Partitioning</u>
**External Fragmentation:** 
- Refers to the phenomenon where free memory blocks are scattered throughout the system, but they are not contiguous.
	- Space wasted external to the allocated memory region.

## Allocation Algorithms

### Classic Approach
**Represent available memory(memory holes) as a linked list**
![[Pasted image 20231127163846.png]]


### First-fit algorithm
1. When a process requests memory, the algorithm searches the available memory blocks starting from the beginning. 
2. The first block that is large enough to accommodate the process is allocated to it.
3. If the selected block is larger than needed, it may be split into two parts.
4. The allocated portion is used for the process, and the remaining part becomes a new free block.
**Cons**
- Increased fragmentation, both internal and external, over time. Small gaps between allocated blocks may accumulate
### Next-fit algorithm
- Memory is allocated to a process starting from the last allocated block and moving forward in a circular manner through the available memory space.
**Pros**
- More uniform allocation
	- More often allocates a block at the end of the memory where the largest block is found
### Best Fit Algorithm

1. When a process requests memory, the algorithm searches for the smallest available memory block that can accommodate the process.
2. Allocates the process to the found block, leaving minimal remaining free space.
3. Helps in minimizing internal fragmentation by fitting processes into the smallest suitable blocks. 

**Cons**
- May lead to more fragmentation over time compared to other algorithms.
- Searching for the best fit can be computationally intensive.

### Worst Fit Algorithm

1. When a process requests memory, the algorithm searches for the largest available memory block.
2. Allocates the process to the found block, leaving larger remaining free space.
3. Aims to minimize the creation of small free spaces for better future allocations. 

**Cons**
- Can result in increased internal fragmentation.
- May not use memory space as efficiently as other algorithms, leading to potential wastage.


## Compaction
- Compaction involves rearranging the allocated and free memory blocks to create a larger, contiguous block of free memory.
- Used to reduce external fragmentation in a computer's memory
![[Pasted image 20231127195338.png|200x300]]

