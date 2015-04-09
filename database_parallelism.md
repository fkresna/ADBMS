# Parallel Databases

There are two main measures of performance of a database system:

1. Throughput, the number of tasks that can be completed in a given time interval
2. Response Time, the amount of time it takes to  complete a single task from the time it is submitted.

Two important issues in studying parallelism:
* Speedup, Running a given task in less time by increasing the degree of parallelism.
* Scaleup, Handling larger tasks by increasing the degree of parallelism

There are two kinds of scaleup that are relevant in parallel database systems, depending on how the size of the task is measured:

* Batch scaleup, The size of the database increases, and the tasks are large jobs whose runtime depends on the size of the database. An example of such a task is a scan of a relation whose size is proportional to the size of the database.
* Transaction scaleup, The rate at which transactions are submitted to the database increases and the size of the database increases proportionally to the transaction rate. This kind of scaleup is what is relevant in transaction-processing systems where the transactions are small updates, For example, a deposit or withdrawal from an account and transaction rates grow as more accounts are created. Such transaction processing is especially well adapted for parallel execution, since transactions can run concurrently and independently on separate processors, and each transaction takes roughly the same amount of time, even if the database grows.

A number of factors work against efficient parallel operation and can diminish both speedup and scaleup

* Startup / shotdown costs. There is a start-up cost associated with initiating a single process. In a parallel operation consisting of thousands of processes, the start-up time may overshadow the actual processing time, affecting speedup adversely
* Coordination / interference costs, Since processes executing in a parallel system often access shared resources, a slowdown may result from the interference of each new process as it competes with existing processes for commonly held resources, such as a system bus, or shared disks, or even locks. Both speedup and scaleup are affected by this phenomenon
* Skew (unbalance tasks) By breaking down a single task into a number of parallel steps, we reduce the size of the average step. Nonetheless, the service time for the single slowest step will determine the service time for the task as a whole. It is often difficult to divide a task into exactly equal-sized parts, and the way that the sizes are distributed is therefore skewed. For example, if a task of size 100 is divided into 10 parts, and the division is skewed, there may be some tasks of size less than 10 and some tasks of size more than 10; if even one task happens to be of size 20, the speed upobtaines by running the tasks in parallel os only five, instead of ten as we would have hoped.

### Parallel Architectures

* Shared memory. All the processors share a common memory
* Shared disk. All the processors share a common set of disks. Shared-disk systems are sometimes called clusters
* Shared nothing. The processors share neither a common memory nor common disk
* Hierarchical. This model is a hybrid of the preceding three architectures

Parallel Database Execution 

* Interquery Parallelism, different queries or transactions execute in parallel with one another. Transaction throughput can be increased by this form of parallelism. However, the response times of individual transactions are no faster than they would be if the transactions were run in isolation. Thus the primary use of interquery parallelism is to scale up a transaction-processing system to support a larger number of transactions per second.
* Intraquery Parallelism referes to the execution of a single query in parallel on multiple processors and disks. Using intraquery parallelism is important for speeding up long-running queries. Interquery parallelism does not help in this task, since each query is run sequentially





Glossary
Throughput, The amount of material or items passing through a system or process