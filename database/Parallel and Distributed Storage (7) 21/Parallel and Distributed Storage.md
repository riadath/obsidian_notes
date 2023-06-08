# <u>I/O Parallelism </u>

Reduce the time required to retrieve relations from disks by partitioning the disks on multiple disks.

## <u>Horizontal Partitioning </u>
records of a relation are divided (or decluttered) among many nodes, such that such that some subset of tuple resides on each node

## <u>Partitioning Techniques</u>
- ### Round Robin
	- Scan relation
	 - Send i'th relation to the node $N_((i-1)mod n + 1)$
- ### Hash Partitioning
	- choose hash function in range (1,n)
	- if hash returns i, send the i'th record to Ni
- ### Range Partitioning
	- Let partition vector be $[v1,v2,v3,v4..., vn]$
	- if $i < j => vi < vj$
	- 
	- Let x be the partitioning attribute (A) value of a record, t\[A\] = x. If $x < v1$, then t goes on node N1 . If $x >= vn-1$ , t goes on node Nn . If $vi <= x < vi+1$, then t goes on node N
	- ![[Pasted image 20230609025913.png | 600]]



### Update on partitioned data
* Insertions : Find appropriate position based on partitioning strategy and insert.
- Deletion: Find location, delete (for round-robin, all partitions are searched.
- If a tuple is updated, its location is not affected if either round-robin partitioning is used or if the update does not affect a partitioning attribute.
- However, if range partitioning or hash partitioning is used;
	- The original tuple is deleted from the original location, and 
	- The updated tuple is inserted and sent to the appropriate node based on the partitioning strategy




## <u>Comparison of Partitioning techniques</u>

### <u>Round Robin</u>
<u>Advantages</u> 
- suited for sequential scan of entire relation on each query
- all nodes have almost equal number of nodes. retrieval work is this balanced between nodes.
<u>Disadvantages</u>
- point and range queries are difficult to process since all n nodes must be used for search
- no clustering. Tuples are scattered evenly across all nodes.

### <u>Hash Partitioning</u>
<u>Advantages</u>
- Useful for sequential scans of the entire relation
- if good hash function -> equal distribution. Retrieval work is well balanced
- best suited for point queries on partition attribute
<u>Disadvantages</u>
- not suitable for point queries on non-partitioning attribute
- not suited for range queries. all nodes need to be scanned
### <u>Range Partitioning</u>

<u>Advantages</u>
- Provides data clustering
- Good for sequential access
- Good for point queries. Only one node needs to accessed. Locate using partition vector
- Range queries on partitioning attribute-> one to a few nodes may need to be accessed. 
<u>Disadvantage</u>
- If many tuples are in the queried range-> I/O bottleneck. Because all the tuples are being retrieved from only a few nodes. 

### ** Partitioning is not useful for small relations which fit into a single disk block or a few blocks**


## <u>Types of distribution skew</u>
1. <mark style="background: #FFB86CA6;">Attribute-value skew</mark>: all tuples with the same value for partitioning attribute end up in the same node resulting in skew.  Occurs in range/hash partitioning. 
2. <mark style="background: #FFB86CA6;">Partition skew</mark>: 
	1. There may be load imbalance even when there's no skew.
	2. if partition vector is not chosen carefully it may assign too many tuples to one single node
	3. less likely with hash partitioning with a good hash function
3. <mark style="background: #FFB86CA6;">Execution Skew:</mark>
	1. if queries tend to access some partitions more often than others.


## <u>Creating a balanced partitioning vector</u>


- ![[Pasted image 20230609042456.png]]

- Can also be done using histograms. 



## <u>Handling Skew (Dynamic Techniques)</u>

### <u>Virtual Nodes</u>
- Consider several times as many (10/20 times) nodes compared to real ones.
- Map tuples and work to these virtual nodes instead of real ones
- Map each virtual node to one of the real node using round robin. E.g.  Virtual node $i$ gets mapped to $(i -1) mod(n) + 1$ . Mapping table can also be used for this.
- Even if one range has too many tuples they would get split across multiple virtual nodes


## <u>Dynamic Repartitioning</u>

- Virtual node approach with a fixed partitioning vector cannot handle significant changes in data distribution over time. Results in some virtual nodes with very large number of tuples or a very high execution load.
- Solution ? 
	- Virtual nodes that are too big can be split 
	- some virtual nodes can be moved from a heavily loaded node to a less loaded node
	- Virtual nodes in this scheme are called tablets


## <u>Routing of queries</u>
- Partition table is stored at a master node + multiple routers
- Queries are sent to routers which forward them to appropriate node
-  **Consistent Hashing**: Works without any master node. Peer to Peer. Distributed hash tables are based on consistent hashing

## <u>Replicas</u>
-  Goal : Avoid data loss. Availability despite node failures. 
- Replicas must be kept consistent on update
- Master Replica Scheme : All updates are sent to master and then replicated to other nodes. \[master might fail]

## <u>Parallel Indexing</u>

![[Pasted image 20230609051008.png]]

### <u>Creating Global Secondary Index</u>
- Given relation r which is partitioned on $K_p$ to create secondary index on attributes $K_i$
	- create a relation $r_i^s(K_i,K_p)$ if $K_p$ is unique, otherwise,
	- $r_i^s(K_i,K_p,K_u)$ where $(K_p,K_u)$ is a key for r
	- Partition $r_i^s$ on $K_i$ 
	- at each node containing a partition of r, create a index on $K_p$ if $K_p$ is a key otherwise create a index on $(K_p, K_u)$
	- Update the relation $r_i^s$ on any updates to $r$ on attributes in $r_i^s$ 


# <u>Distributed file systems</u>

## Basic Architecture
![[Pasted image 20230609051903.png]]

### HADOOP File System (HDFS)
![[Pasted image 20230609054008.png]]
- HDFS is modeled after GFS (Google file system)
- Data Coherency
	- 'Write once ready many' access model
	- Client can only append to existing files
- Client : Finds location of  blocks form NameNode, Accesses data directly from DataNode


### <u>Limitations of HDFS</u>
- Central master becomes bottleneck
- File system directory overhead per file
- File system do not provide consistency guarantee

## <u>Data Storage System vs Databases</u>

![[Pasted image 20230609054631.png]]

