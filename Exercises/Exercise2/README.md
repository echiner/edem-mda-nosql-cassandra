# Exercise 2: Creating a Data Model

## Initial setup

Just follow the steps defined in the home page, but we won't need the CQL console anymore, since we will be using Zeppelin from now on.

Go to the Zeppelin URL: http://localhost:9999

Configure the Cassandra interpreter so it points to Cassandra:

1. Open the "Interpreter" configuration (right hand side, under "anonymous")
2. Search for "cassandra"
3. Click "Edit", update the "cassandra.hosts" to "cassandra" (previously "localhost"), and restart the Interpreter
4. Create a new note ("Notebook" menu on the top --> "+ Create new note"). You can select "cassandra" as the default Interpreter

## Exercise

Let's start by testing some of the logic done before. So try commands to do the following:

* Get the help
* List the keyspaces
* List the tables
* Query the previously crated table

And now we will create a couple of tables for the following use case: **Messaging System**.

### Use Case: Messaging System

**Description**:

We want to create the tables required for a persistent messaging system similar to WhatsApp.

**Features**:

* We need to store all messages
* The user has the ability to create groups
* Access patterns:
  * Send a message (store a single message) in a conversation or group
  * Retrieve all messages from a conversation
  * Retrieve all messages from a group
  * Remove a single message

**Deliverable**:

* DDL scripts for the required table(s)
* Explanation of the data model