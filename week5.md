# Indexing

### Organization of Records in Files

* Heap - a record can be placed anywhere in the file where there is space; stored in no particular order
* Sequential - store records in sequential order, based on the value of the search key of each record
* Hashing - a hash function computed on some attribute of each record; the result specifies which block of the file the record should be placed
	* Ideal hash function is uniform and random - buckets contain same number of records


### Index
An index is an optional structure associated with a table or table cluster, that can sometimes speed data access. By creating an index on one or more columns of a tablem you gain the ability in some cases to rettieve a small set of tandomly distributed rows from the table. Indexes are one o many means of reducing disk I/O.

If a heap-organized table has no indexes, then the database must pergorm a full table scan to find a value. For example, without an index, a query of location 2700 in the hr.departments table requires the atabase to search every tow in every table block gor this value. This approach does not scale well as data volumes increase.

Pros :

* Can speed up access to desired data
* Typically much smaller than original table

Cons :

* Requires additional storage
* Requires additional accesses for retrieval
* Must be updated with database

There are 2 basic kind of indices :

* Ordered Indices, Based on a sorted ordering of the values
* Hash Indices, Based on a uniform distribution of values across a range of buckets. The bucket to which a value is assigned is determined by a function, called a *hash function*

### Ordered Indices
There are two types of ordered indices that we can use :

* Dense index : In a dense index, an index entry appears for every search-key value in the file.
* Sparse index : In a sparse index, an index entry appears for only some of the search-key values. 


Seconday index can't be sparse it must be dense

### Index Data Structures
B+ trees are the most widely used index (typically default)

* Index-Sequential Files
	* Performance degrades as new overflow nodes are added
	The entire file must be periodically re-organized (expensive)
* B+ Tree Index
	* Performance is maintained as the structure grows
	* Tree is constantly re-organized (re-balanced) with localized changes resulting form insertions and deletions
	* No structure-wide re-organization; a big advantage

#### B+ Trees
Pros :

* Balanced tree
* Good for high cardinality attributes
* Good for point and range queries

Cons :

* Requires some overhead when inserting and deleting
* Also requires some space overhead
* Advantages of B+ trees greatly outweigh disadvantages

B+ Tree

* Root Node
* Internal Node
* Leaf Node

#### When to use an index?

* Have an index on the primary key, since this will often be used for access
	* Generally created automatically in Oracle (as are indexes on columns with a UNIQUE constraint)
* Specify indices for foregin keys that are used for joining tables
* Index on non key attributes that are used frequently for selection criteria or groupong
* Not all tables may need an index (e.g small tables)
* Drop any indexes not being used
	* Read / write tradeoff
		* Tables can have many indexes, but more indexes mean more overhead as the table is modified (write operations)
		* However, more indexes (especially targeted for espensive queries) can improve data retrieval for read operations
	* Indexes take up storage space. Multiple indexes? Can result in considerable amount of storage.

### Glossary 
**High-Cardinality** refers to columns with values that are very uncommon or unique. High-cardinality column values are typically identification numbers, email addresses, or user names. An example of a data table column with high-cardinality would be a USERS table with a column named USER_ID. This column would contain unique values of 1-n. Each time a new user us created in the USERS table, a new number would be created in the USER_ID column to identify them uniquely. Since the values held in the USER_ID column are unique, this column's cardinality type would be referred to as high-cardinality.

**Normal-cardinality** referes to columns with values that are somewhat uncommon. Normal-cardinality column values are typically names street addresses, or vehicle types. An example of a data table column with normal-cardinality would be a CUSTOMER  table with a column named LAST_NAME, containing the last names of customers. While some people have common last names, such as Smith , others have uncommon last names. Therefore, an examination of all of the values held in the LAST_NAME column would show "clumps" of names in some places (e.g.: a lot of Smith's) surrounded on both sides by a long series of unique values. Since there is a variety of possible values held in this column, its cardinality type would be referred to as normal-cardinality.

**Low-cardinality** refers to columns with few unique values. Low-cardinality column values are typically status flags, Boolean values, or major classifications such as gender. An example of a data table column with low-cardinality would be a CUSTOMER  table with a column named NEW_CUSTOMER. This column would contain only 2 distinct values: Y or N, denoting whether the customer was new or not. Since there are only 2 possible values held in this column, its cardinality type would be referred to as low-cardinality

Sparse :
 
* present only in small amounts : less than necessary or normal; especially 
* Thinly covering an area : not thick or full

Dense :

* having parts that are close together
* crowded with people
* not smart : not able to understand things easily

Coalesce : to come together to form one group or mass

### Reference 
<http://docs.oracle.com/cd/E11882_01/server.112/e40540/indexiot.htm#CNCPT721>
<http://docs.oracle.com/cd/E11882_01/server.112/e25494/indexes.htm#ADMIN016>