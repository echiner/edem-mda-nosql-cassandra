# Exercise 1: Basic syntax

## Initial setup

Just follow the steps defined in the home page, and enter the CQL console.

## Exercise

Let's start by understanding the environment:

```shell
# Get some help
cqlsh> help

# List the existing keyspaces
cqlsh> describe keyspaces;

# Show the available tables (mainly system tables)
cqlsh> describe tables;

# Basic query (from "system.local" table)
cqlsh> SELECT cluster_name, listen_address, release_version FROM system.local;

# Create a new keyspace
cqlsh> CREATE KEYSPACE edem WITH  replication = {'class': 'SimpleStrategy', 'replication_factor' : 3};
# A warning will be shown (since we only have a node) --> Fix it (drop keyspace and recreate with correct replication factor)

# Create a new table
cqlsh> CREATE TABLE edem.students (
    studentid uuid,
    name text,
    age int,
    PRIMARY KEY (studentid)
);

# Query it
cqlsh> select * from edem.students;

# Let's insert some data
cqlsh> insert into edem.students (studentid, name, age) values (now(), 'John Doe', 25);
cqlsh> insert into edem.students (studentid, name, age) values (now(), 'Alice', 22);
cqlsh> insert into edem.students (studentid, name, age) values (now(), 'Bob', 22) USING TTL 30;

# And query (several times, for example try again in 1 minute)
cqlsh> select * from edem.students;
```

**Exercise 1**:

Take a look at the documentation (https://cassandra.apache.org/doc/4.0/cassandra/cql/index.html) and understand what we are doing.
We are specially interested in the following:

* **Data Types**: https://cassandra.apache.org/doc/4.0/cassandra/cql/types.html#native-types
* **Keyspace creation**: https://cassandra.apache.org/doc/4.0/cassandra/cql/ddl.html#create-keyspace-statement
* **Table creation**: https://cassandra.apache.org/doc/4.0/cassandra/cql/ddl.html#create-table-statement
* **Insert data**: https://cassandra.apache.org/doc/4.0/cassandra/cql/dml.html#insert-statement

**Exercise 2**:

Discuss in the class what happened in the following cases:

1. When we created the keyspace
2. With the data we inserted