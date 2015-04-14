# Distributed Database

### Homogeneous and Heterogeneous Databases

In a homogeneous distributed database system, all sites have identical database management system software, are aware of one another, and agree to cooperate in processing users requests. 

In a heterogeneous distributed database, different sites may use different schemas, and different database-management system software. The sites may not be aware of one another, and they may provide only limited facilities for cooperation on transaction processing. The differences in schemas are often a major problem for query processing, while the divergence in software becomes a hindrance for processing transactions that access multiple sites.

### Data Distribution Strategies

* Centralized
	* All data located at a single site
* "Pure" distributed database
	* Single copy of data in entire system.
* Replicated
	* Multiple copies of data, stored at different sites.
* Fragmanted
	* Database is divided into non-overlapping partitions, each located at a different site.
* Hybrid Approach
	* Critical partitions are replicated, remaining partitions are located at a individual sites.