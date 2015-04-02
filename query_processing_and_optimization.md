# Query Processing and Optimization

## Query Processing
Query processing refers to the range of activities involved in extracting data from a database. The activities include translation of queries in high level database languages into expressions that can be used at the physical level of the file system, a variety of query-optimizing transformations, and actual evaluation of queries.

Query Cost: The cost is an estimated value proportional to the expected resource use needed to execute the statement with a particular plan. The optimizer calculates the cost of access paths and join orders based on the estimated computer resources, which included I/O, CPU, and memory

How do we measure query cost?

* I/O Cost
* Computation Cost
* Memory Usage
* Communication cost (network traffic), memory buffer size, number of CPUs, storage architecture, data distribution, network speeds, traffic patterns, query selectivity

The query optimizer operations include:

* Query Transformation
* Estimation
* Plan Generation

### Query Transformation 
Technique:

* View Merging
* Predicate Pushing
* Subquery Unnesting
* Query Rewrite with Materialized Views

### Estimation
The estimator determines the overall cost of a given execution plan. The estimator generates three different types of measures to achieve this goal:

* Selectivity, This measure represents a fraction of rows from a row set. The selectivity is tied to a query predicate, such as last_name='Smith', or a combination of predicateds
* Cardinality, This measure represents the number of rows in a row set
* Cost, This measure represents units of work or resource used. The query optimizer uses disk I/O, CPU usage, and memry usage as units of work.

### Plan Generation
The plan generator explorers various plans for a query block by trying out different access paths, join methods, and join orders. Many plans are possible because of the various combinations of different access paths, join methods, and join orders that the database can use to produce the same result. The purpose of the generator is to pick the plan with the lowest cost.

## Query Optimization

Query optimization is the process of selecting the most efficient query-evaluation plan from among the many strategues useally possible for processing a given query, especially iif the query is complex. We do not expect users to write their queries so that they can be processed efficiently, Rather, we expect the system to construct a query-evaluation plan that minimizes the cost of query evaluation.

A materialized view is like a query with a result that the database materializes and stores in a table. When the database finds a user query compatible with the query associated with a materialized view, then the database can rewrite the query in terms of the materialized view. This technique improves query execution because most of the query result has been precomputed.

### Glossary

Full table scan: A scan of table data in which the database sequantially reads all rows from a table and filters out those that do not meet the selection criteria. During full table scans the database scans all data blocks under the high water mark.

Hash join, A join in which the database uses the smaller of two tables or data sources to build a hash table in memory. In hash joins, the database scans the larger table, probing the hash table for the addresses of the matching rows in the smaller table.

