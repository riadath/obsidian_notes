# <u>File and Storage</u>
### Raid
Redundant array of independent disks. Making use of two or more HDD to improve performance, reliability or create larger data volumes.

### Mirroring
Simplest but most expensive approach to introduce redundancy is to duplicated every disk.

### Stripping
**Bit Level Stripping** : Strip every bit of every byte across multiple disks
**Block level Stripping** : Strip blocks of data across multiple disks

- RAID 1 is used for storage for log files in a database, because for storing log files, fault tolerance is needed on a limited volume of data.

### File organization types

- **Heap file organization**: Any record can be placed anywhere in the file where there is pace for the record. There is not ordering of records. Typically, a single file for each relation.
- **Sequential file organization**: Records are stored in a sequential order. based on the value of a search key of each record.
- **Hashing File Organization**: A hash function is computed on some attribute of each record who's result is specifies in which block the record should be stored
- **Multiple clustering file organization**: Records of several different relation can be stored in the same file. Related records of the different relations are sorted on the same block so that one I/O operation fetches related records from all  the relations. 

### Reorganization
The sequential file organization will work if only a small number of records need to be stored in the overflow blocks. Eventually the correspondence between search key order and physical order may be totally lost. In such case sequential processing will become much less efficient. At this point, the file should be reorganized so that it is once again physically in sequential order.



### Slotted page structure 
![[Pasted image 20230609221808.png]]

**Header Stores**:
- No of record entries in the header
- The end of free space in the block
- An array who's entries contain the location and size of each records

*slotted page structure requires that there be no pointers that point directly to records. Instead, pointers must point to the entry in the header that contains the actual location of the record.*


**Storing each relation in one file**: Can use the file system provided by the OS thus simplifying the DBMS but restricts the ability to increase performance by using more sophisticated storage structures. 

**Storing multiple relation in one file**: Complex structures can be implemented through the DBMS but increases the size and complexity of the DBMS.

**Seek Time**: The time it take for a disk read/write head to move to a specific location / data track is called seek time.

# <u>Indexing and Hashing</u>

**Search Key**: An attribute or set of attributes used to look up records in a file called a search key.

**Primary/Clustering Index**: If the file containing the records is sequentially ordered a,  primary index is an index whose search key also defines the sequential order of the file. There can only be one primary index for a relation. *dense/sparse*
**Secondary/Non Clustering Index**: Indices whose search key specifies an order different from the sequential order of the file are called secondary indices. There can be multiple secondary indices. *only dense. dis: impose a significant overhead on modification of the database*

**Index-Sequential Files**: Files that are ordered sequentially on some search key and have a primary index on the search key. *dis: performance degrades as the files grows.* 

**Dense Index**: a index record appears for every search key value in the file. Faster to locate files.
**Sparse Index**: index record appears for only some of the search key values. Require less space.

**Multilevel Index**: An index with two or more levels is called a multilevel index. Requires fewer I/O operations. 

**B+ Tree**: a type of index in the form of a balanced tree in which every path from the root to a leaf node is of the same length.  Leaf contains between $ceil(n/2)$   and $n$ children. Each leaf has between $ceil((n-1)/2)$ and $n-1$ values.  *dis: performance overhead on insertion and deletion. Space overhead*

### B+ tree vs B tree
search keys may appear twice | search key only appears once
contains redundant storage of search-key values | eliminates redundant storage
Takes more space | takes less space
no additional pointer for search key | additional pointers for each search key in non leaf nodes


### Estimated size of the bucket
$(n_r/f_r) * (1 + d)$  
Here d is the fudge factor

### Handling Bucket Overflows
**Closed Hashing**: put records into overflow buckets
Open Hashing: Linear Probing, Quadratic Probing, Double Hashing



# <u>Data Analytics</u>

## <u>OLAP</u>

- Online Analytical Processing: Swiftly answer multi-dimensional analytical queries.
- MOLAP : Stores data cube instead of relational database. Better performance. Less Storage
-  ROLAP : Stores relational databases. More scalable. Large volume of data difficult to process.
-  HOLAP : Hybrid of MOLAP and ROLAP

### Operations of OLAP
- Visualization of data, using Cross-Tabs or data cubes
- Pivoting : Changing dimensions used in cross tabs.
- Display data at any level of granularity
- Drill Down, rollup, slicing, dicing

### Measure Attribute
Attributes that measure some value i.e. number of sales, item quantity

### Dimension Attribute
All the other attributes that define the dimensions on which measure attributes are viewed. For example in  a sales relationship, item_name, color, size etc.

### Concept Hierarchy
A hierarchically organized collection of different levels of detail for an attribute (or concept) is called a concept hierarchy. 

## <u>Cube and Rollup</u>

sales(item_name,color,size,number)
**Cube**: Computes the union of all possible different groupings of a relation.

E.g.  select item_name, color, size, sum(number)
from sales
group by cube(item_name, color, size)

**Rollup**: Generates aggregates at multiple levels of hierarchy

E.g. select item_name, color, size, sum(number)
from sales
group by rollup(item_name, color, size)

# <u>Data Warehouse</u>
- A data warehouse is a repository or archive of information gathered from multiple sources, stored under a unified schema, at a single site.
- ![[Pasted image 20230610004821.png]]


### <u>Components of a data warehouse</u>
- Database Servers
- Queries/Reports
- OLAP/Multidimensional Analysis
- Data mining
### <u>Features of a data warehouse</u>
- Subject Oriented
- Integrated
- Time-Variant
- Non-volatile
- Data granularity


### Source Driven architecture
- Transfer initiated by the source
- Data can be propagated as soon as it is available
- Source does not need to keep historical information
### Destination Driven architecture
- The destination probes the source for data
- Source does not have to be active all the time
- Easier to implement
- Warehouse has more control on when to carry out data gathering activities

## <u>Steps to build a warehouse</u>
- Identify the data source
- Build customized ETL tool 
	- *The different steps involved in getting data into a data warehouse are called as extract, transform and load or ETL tasks; extraction refers to getting data from the sources, while load refers to loading the data into the data warehouse.*
- Extraction
- Transformation
- Loading

### <u>Fact Table</u>
Tables containing multidimensional data
### <u>Dimension Table</u>
Stores additional data

### <u>Star Scheme</u>
With one fact table and multiple dimension table and a foreign key from the fact table to the dimension table
### <u>Snowflake Schema</u>
Star schema with multiple levels of dimension tables


# <u>Data Mining</u>
- The process of semi-automatically analyzing large databases to find useful patterns.
### <u>Application of data mining</u>
- Prediction 
- Association

### <u>Support</u>
- Support is a measure of what percentage of the population satisfies both the antecedent and the consequent of the rule.
- **Minimum Support(minsup)**: An itemset satisfies a minimum support if its frequency count is greater than or equal to a specific support count, min_sup.
- if min_sup = 50%, sup(A,C) = 50% >= 50%, (A,C) is frequent
### <u>Confidence</u>
- Measure of how often the consequent is true when the antecedent is true.
### Finding Association using apriori algorithm
- Find all frequent itemsets
- Generate strong association rules from the frequent itemsets found that have minimum confidence.



# <u>Query Processing Formulas</u>
Linear Search : $t_s + b_r * t_t$
