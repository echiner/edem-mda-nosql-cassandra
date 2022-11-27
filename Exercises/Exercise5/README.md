# Optional: Testing other NOSQL (Neo4j and MongoDB)

## Introduction

In this optional exercise we will be testing two more NOSQL database we have viewed during the course:

* **Neo4j**: Graph database management system developed by Neo4j, Inc. Described by its developers as an ACID-compliant transactional database with native graph storage and processing.
* **MongoDB**: Cross-platform document-oriented NOSQL database program.MongoDB uses JSON-like documents with optional schemas.

## Graph Database: Neo4j

![Neo4j Logo](../../img/neo4j-logo.png)

First we will run the latest version of Neo4j using Docker:

```
docker run --name testneo4j -p7474:7474 -p7687:7687 -d --env NEO4J_AUTH=neo4j/test --env NEO4J_dbms_connector_https_advertised__address="localhost:7473" --env NEO4J_dbms_connector_http_advertised__address="localhost:7474" --env NEO4J_dbms_connector_bolt_advertised__address="localhost:7687" neo4j:latest
```

Now go to the database's UI: http://localhost:7474/browser/

When asked to "Connect to Neo4j", leave everything as default except for:

* Username: neo4j
* Password: test

In the home page, you can choose from the different guided tutorials:

* Getting started with Neo4j Browser: If you want to lear the basics
* Try Neo4j with live data (RECOMMENDED): Test the database with real data from movies/actors
* Cypher basics: Learn the basics of Cypher, the Neo4j query language

### Using the command line

If you like text better or the UI is not working, you can also use the Cypher shell directly by following these steps:

* Get into the Neo4j docker container:

```
docker exec -it testneo4j bash
```

* Launch the Cypher shell:

```
cypher-shell -u neo4j -p test
```

* Test with a simple command (list the number of nodes in the database):

```
MATCH (n) RETURN count(n);
```

The above query will return '0' since we don't have any data. So now feel free to add data, query and play around.

### Reference

* [Neo4j](https://neo4j.com/)
* [Running Neo4j in Docker](https://neo4j.com/developer/docker-run-neo4j/)

## Document Database: MongoDB

![MongoDB Logo](../../img/mongodb-logo.png)

For this part we have created a simple Docker Compose with two components:

* **MongoDB**: The document database itself.
* **Mongo Express**: User interface for interacting with the database.

So first we will launch the components using Docker Compose:

```
docker compose -f docker-compose-mongo.yml up -d 
```

Now just go to Mongo Express UI: http://localhost:8081/

For the time being, only technical databases are available. You can take a look at them by clicking on the "View" buttons. NOTE: **Do not delete any of those databases!!**.

Now we will **create a new database** for testing purposes by adding the name on the top-right-hand corner and clicking on "Create Database". Then just click on the newly created database.

We will then **create a collection** (similar to a table in SQL databases) by adding the collection name (e.g. "pokemon") on top-right-hand corner and clicking on "Create collection".

And now **import the data**. For this example we be loading a dataset with Pokemon and their abilities. For doing so, follow these steps:

* Enter the database created before. You should only see a "detele_me" collection and the one created above.
* In the one you created, click on "Import" button. Then look for "pokemon-dataset" file in this exercise's folder 
* Click on the "View" button or just on the collection name and you should see all the data

Now let's do a couple of **simple queries**. In the "Find area" on top, do the following:

* Look for Pikachu:
  * Key: name.english
  * Value: Pikachu
* Look for all pokemon of the type "Fire":
  * Key: type
  * Value: Fire

When you set the above and click on "Find" it will show the documents found with that criteria.

You can also go to a specific document by the path and document ID. For example, for document ID "143" in the "pokemon" collection and "edem" database:

http://localhost:8081/db/edem/pokemon/143

### Reference

* [MongoDB](https://www.mongodb.com/home)
* [MongoDB Documentation](https://www.mongodb.com/docs/)
* [Mongo Express](https://github.com/mongo-express/mongo-express)
* [Running MongoDB using Docker](https://www.mongodb.com/compatibility/docker)
* [Compass](https://www.mongodb.com/products/compass): Alternative to Mongo Express.