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