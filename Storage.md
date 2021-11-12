## **Physical Storage**

3-level storage hierarchy

* Primary storage

  * e.g., RAM: main memory, cache;
* Secondary storage

  * e.g., hard-drive disks (HDD), solid-state disks (SSD);
* Tertiary storage

  * e.g., optical drives.

As we go down the storage hierarchy

- Storage capacity: increases

- Access speed: decreases
- Money-costs: decreases

Fundamental Limitation: Database is too large to fit in RAM

* By default, data lives on secondary storage

But the CPU cannot directly access data not in RAM

* Data must first be loaded into main memory from secondary storage…
* … then fetched into registers to be processed

 Secondary storage access time becomes the bottleneck

* Data access takes about 10ms-60ms, instead of 30-120ns

## **Organisation-based Optimisation**

Challenge: Organise tuples on the disk to minimizing I/O accesses

* Logical Representation

  * Represent a Tuple of a relation as a record
  * DB data is a set of records; each record is a set of attributes
  * Records are grouped together forming a file
* Records can be of:

  * Fixed length; i.e., the size is pre-determined by the designer
  * Variable length; i.e., the size of each attributes varies, e.g., some fields are optional with size >= 0 bytes

## Blocking Factor

Physical Representation

* Records are stored in blocks
* Blocks are of fixed-length, normally 512 bytes to 4096 bytes

Consider a record of R bytes and a block of B bytes.

Blocking factor (bfr): The number of records stored in a block (i.e., records per block)

* bfr = ⎣B/R⎦ or floor(B/R)
* e.g., bfr = 100 records per block 🡺 a block can store up to 100 records

## **Blocks to Files on Disk**

File is a set of blocks, and each block a set of records

How do we allocate blocks to files?

* Contiguous (neighboring) allocation: A file contains spatially consecutive blocks (a.k.a. self-navigation file)
* Linked allocation: Each block i has a pointer to the logically next block i+1 anywhere on the disk -- i.e., a linked list of blocks; navigation information is stored in each block of the file
* Indexed allocation: there exists a specific block (index block -- can be anywhere on the disk), which maintains a list of pointers pointing to the physical address of each block; navigation information stored in the index block

## **File Structures for Database Data**

**Challenge: Distribute records in a file to minimize I/O cost**

Options:

* Heap Files, a.k.a. unordered files

  * Principle: new records are added at the end of the file, i.e., at the end of the last block (append)
* Ordered Files, a.k.a. sequential files
* Principle: records are kept sorted based on ordering field; if it is a key, it is called ordering key
* Hash Files
* Principle: a hashing function y = h(x) is applied to each record field x (hash field or hash key if it is a key)
* The output y refers to the block id which contains record x 🡺 mapping a record to a block

Given a file structure, we measure I/O cost for:

* Retrieving a record x according to a searching field from disk to memory (retrieval/search cost)
* Inserting/deleting/updating a record x from memory to the disk (update cost)

Cost Function: # of block accesses (read/write) to search/insert/delete/update record x

### **Heap File**

Inserting a new record is efficient:

* Retrieve (load from disk to memory) the last block (addresses are kept at file header)
* Insert the new record at the end of the block and write the block back to disk
* Complexity: O(1) block access...

Retrieving a record is slow -- essentially, linear search through all the b file blocks

* Retrieve each block from disk to memory
* Search in-memory for the record
* Repeat until EOF…
  * On average, we access ~ b/2 blocks
  * We access b blocks if the record is not in the file
* Complexity: O(b) block accesses

Deleting a record is slow:

* Find and load the block containing the record
  * Remove data from the block and write the block back to disk 🡺 creates “holes” in blocks
* Complexity: O(b) + O(1) block accesses
* Alternatively, use deletion markers (aka tombstone records) instead (set a bit from 0 to 1)
* Periodically, the storage space for the file is re-organised/compacted

### **Sequential File**

Retrieval:

* Retrieve a record using the ordering field: efficient

  * The right block can be found using binary search on the ordering field over a file with b blocks
  * Complexity is O(log2b)
* Retrieve a record using a non-ordering field: inefficient
* We do not exploit the record ordering 🡺 equivalent to a heap file
* Complexity is O(b) -- i.e., linear search
* Range queries?
* Efficient if on ordering field, otherwise inefficient
* Methodology:
* Using binary search, find the block which contains the record for the lower bound 🡺 O(log2b)
* Then, fetch contiguous blocks until the record containing the upper bound is located 🡺 O(b)
* Complexity: O(log2b) + O(b) block accesses

  = O(b)…

Insertions:

* Expensive!
  * Using binary search, locate the block where the record should be inserted, then move all subsequent records to make room for the new one
  * On average, half of the records must be moved to make room for the new record -- very expensive, especially for large files!
* Alternative with chain pointers
* If there is free space in the right block, insert the new record there, else insert the new record in an overflow block and use chain pointers -- pointer chain must be updated (akin to an on-disk sorted-linked list)

Deletions:

* Are expensive
  * Using binary search, locate the block where the record is to be deleted; binary search
  * Adopt deletion markers and update the pointer not to point to the deleted record
  * Periodically: reorganise/re-sort the file to restore the sequential order (invoke: external sorting… expensive)

Updates:

* On the ordering field value are costly
  * Record deleted from its old position & inserted into its new position in the file
* On a non-ordering field value are efficient!
* Complexity is O(log2b) + O(1) block accesses

### **Hash File**

Idea: Use hashing

* Partition (quantize) the records into M buckets: bucket 0, ..., bucket M-1 using a hash function y = h(k) with output y ∈ {0, 1, …, M-1}

  * Each bucket can have more than one blocks
* h(k) has to uniformly distribute its input values over the M buckets
* i.e., given a value k, each bucket will be chosen with equal probability 1/M
* y = h(k) = k mod M
* Mapping a record x to a bucket y = h(x.k) is called external hashing
* Also called indirect clustering: group tuples together w.r.t. their hashed-values and not their hash-field values
* Normally, collisions occur! i.e., two or more records are mapped to the same bucket!
* Example: Let M = 3, h(k) = k mod 3 ∈ {0, 1, 2}, thus, we obtain three buckets
* The records with k = 3, 11, 2, and 4 are stored in buckets 0, 2, 2, and 1, resp. 🡺 collision on bucket 2

#### **External Hashing**

Deletions:

* Deleting a record x based on the hash field k is easy
  * If record x is in the main bucket then delete it from there immediately: O(1)
  * Note: We may need/want to move a record from the overflow bucket to the main bucket upon deletion
* Deleting a record based on a non-hash field?
* Requires scanning all records to identify those with that value… Expensive!

Updates:

* Updating the value of a non-hash field m ≠ k of a record x is easy

1. Locate record x in its main or overflow bucket(s)
2. Load block into memory, update it, and write it back

* O(1) or O(1) + O(n) block accesses
* Updating the value of the hash field k (to k’) for a record x a bit more complicated

  * Deletion of old record in O(1)

Insertion to the new bucket referred to by h(x.k’) in O(1) in the best case
