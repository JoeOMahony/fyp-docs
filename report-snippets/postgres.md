# PostgreSQL Relational Database

PostgreSQL, or Postgres, is an open-source object-relational database management system that allows for a wide variety of data types while retaining ACID-compliant transactions. Postgres is natively designed to run on a single node, primarily handling concurrency through saving before-and-after snapshots of any row modified in a transaction (Multi-Versioned Concurrency Control), but falling back on a modified implementation of traditional RDBMS pessimistic locking (strict 2-phase locking with the DDL for queries to skip or wait for lock release). Neon, a managed, serverless database platform for Postgres, uses this model for concurrency control on each branch's primary compute node while providing for scalability and data resilience through a distributed storage system. Postgres was selected over a NoSQL solution due to its native support for JOINs and the need to enforce a schema in processed training data. Compared to other RDBMS', I chose Postgres due to its open source licence helping to lower costs and mitigate vendor lock-in through enabling provider competition, my familiarity with relational databases and SQL commands, and its wide range of available data types.

https://www.postgresql.org/about/
https://www.percona.com/blog/what-is-postgresql-used-for/
https://www.postgresql.org/docs/8.4/transaction-iso.html
https://www.geeksforgeeks.org/dbms/what-is-multi-version-concurrency-control-mvcc-in-dbms/
https://www.geeksforgeeks.org/dbms/what-is-multi-version-concurrency-control-mvcc-in-dbms/
https://neon.com/blog/get-page-at-lsn
https://www.tinybird.co/blog/postgres-vs-sqlite
