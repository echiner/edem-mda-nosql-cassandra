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
cqlsh> CREATE KEYSPACE dlp WITH  replication = {'class': 'SimpleStrategy', 'replication_factor' : 3};

# Create a new table
cqlsh> CREATE TABLE dlp.students (
    studentid uuid,
    name text,
    age int,
    PRIMARY KEY (studentid)
);

# Query it
cqlsh> select * from dlp.students;

# Let's insert some data
cqlsh> insert into dlp.students (studentid, name, age) values (now(), 'John Doe', 25);
cqlsh> insert into dlp.students (studentid, name, age) values (now(), 'Alice', 22);
cqlsh> insert into dlp.students (studentid, name, age) values (now(), 'Bob', 22) USING TTL 30;

# And query (several times)
cqlsh> select * from dlp.students;
```

**Exercise 1**:

Take a look at the documentation (http://cassandra.apache.org/doc/3.11/cql/index.html) and understand what we are doing.
We are specially interested in the following:

* Data Types: http://cassandra.apache.org/doc/3.11/cql/types.html#native-types
* Keyspace creation: http://cassandra.apache.org/doc/3.11/cql/ddl.html#create-keyspace
* Table creation: http://cassandra.apache.org/doc/3.11/cql/ddl.html#create-table
* Insert data: http://cassandra.apache.org/doc/3.11/cql/dml.html#insert