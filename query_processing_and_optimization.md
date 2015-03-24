# Query Processing and Optimization

Query processing refers to the range of activities involved in extracting data from a database. The activities include translation of queries in high level database languages into expressions that can be used at the physical level of the file system, a variety of query-optimizing transformations, and actual evaluation of queries.

Query Cost: The cost is an extimated value proportional to the expected resource use needed to execute the statement with a particular plan. The optimizer calculates the cost of access paths and join orders based on the estimated computer resources, which included I/O, CPU, and memory

How do we measure query cost?

* I/O Cost
* Computation Cost
* Memory Usage
* Communication cost (network traffic), memory buffer size, number of CPUs, storage architecture, data distribution, network speeds, traffic patterns, query selectivity

The query optimizer operations include:

* Query Transformation
* Estimation
* Plan Generation

Query Transformation Technique:

* View Merging
* Predicate Pushing
* Subquery Unnesting
* Query Rewrite with Materialized Views

Estimation
The estimator determines the overall cost of a given execution plan. The estimator generates three different types of measures to achieve this goal:

* Selectivity, This measure represents a fraction of rows from a row set. The selectivity is tied to a query predicate, such as last_name='Smith', or a combination of predicateds
* Cardinality, This measure represents the number of rows in a row set
* Cost, This measure represents units of work or resource used. The query optimizer uses disk I/O, CPU usage, and memry usage as units of work.