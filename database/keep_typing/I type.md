### Raid
Redundant array of independent disks. Making use of two or more HDD to improve performance, reliability or create larger data volumes.

### Mirroring
Simplest but most expensive approach to introduce redundancy is to duplicated every disk.

### Stripping
**Bit Level Stripping** : Strip every bit of every byte across multiple disks
**Block level Stripping** : Strip blocks of data across multiple disks

- RAID 1 is used for storage for log files in a database, because for storing log files, fault tolerance is needed on a limited volume of data.

### File organization types

- **Heap file organization** : Any record can be placed anywhe