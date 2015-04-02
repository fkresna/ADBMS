# Transaction Processing

A transaction is a logical unit of work that includes one or more executable statements which may access or update a collection of data items

Main isses
* What to do when a failure occurs?
* Concurrent execution of multiple transactions. How DBMS can be exexuted at the same time, a lot of people doing a lot of transaction at almost the same time.

ACID Properties of Transactions

* **Atomicitiy**, A transaction is a complete unit of work - all or none of the operations are reflected in the database, no partial execution
* **Consistency**, A transaction's correct execution takes the database from one consistent state to another
* **Isolation**, Each transaction must appear to execute by itself without interference from other concurrrent transactions
* **Durability**, A successful transaction results in database changes that persist, even in the face of system failures




### Concurrency Control 

Concurrency Control, Controlling simultaneous access/update of a single datbaase of multiple users

Why Concurrency?

* Better transaction throughput
* Reduce waiting time

Better performance

Why concurrency control?

* Transactions submitted by one user interfering with another transaction can generate incorect or inconsistent results

ANSI/ISO Transaction Isolation Levels

* Read uncommitted
* Read commited
* Repeatable read
* Serilizable

Concurrency Problems:

* Write Problems
	* Lost Update, Two transactions trying to update the same database item at about the same time. Results of one transaction overwrites the results of the other 	
* Read Problems
	* Dirty reads, A transaction reads data that has been written by another transaction that has not been commited yet
	* Nonrepeatable (fuzzy) reads, A transaction rereads data it has previously read and finds that another commited transaction has modified or deleted the data. For example, a user queries a row and then later queries the same row, only to discover that the data has changed.
	* Phantom reads, A transactions reruns a query returning a set of rows that satisfies a search condition and finds that another commited transaction has inserted additional rows that satisfy the condition. For example, a transaction queries the number of employees. Five minutes later it performs the same query criteria than before, but unlike in a fuzzy read the previously read data is unchanged.

Cascading Rollbacks, Transaction failure leads to a series of transaction rollbacks

Concurrency Control Methods

* Locking
* Timestamps
* Multiversion concurrency control
	* Two-phase locking version
	
#### Locking 

Lock, a mechanism to control concurrent access to a data item by competing transactions

How it works:

* Transactions wanting to read/change a data item requests the lock manager to lock the data they want to read/change
* Lock Manager locks the requested data items for the use of the requesting transaction
* When the first transaction is done with the lock, The lock is released. Data is now available for the next transaction
* Lock manager maintains a "lock table" to record granted locks and pending requests, which is used for lock management

Glossary

* Granularity, The scale or level of detail present in a set of data or other phenomenon.
* Concurrency, a situation in which two or more things happen at the same time
* Serializability is the major correctness criterion for concurrent transactios executions. It is considered the highest level of isolation between transactions, and plays an essential role in concurrency control. 