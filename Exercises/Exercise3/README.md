# Exercise 3: Inserting and reading data

## Initial setup

With the setup from the previous exercises should be enough to perform this exercise.
You will need:

* Apache NiFi running: http://localhost:8888/nifi
* Apache Zeppelin running: http://localhost:9999
* Cassandra running

## Exercise

In this exercise we will simulate a simple **IoT project**, gathering data using NiFi, storing it in Cassandra and run some basic queries in Zeppelin.

### Development

First we will create the table which will store the sensor data. This is the data we want to store:

* **Machine ID**: Identifies the machine we are gathering data from (there can be many)
* **Sensor ID**: Identifies which sensor (from a machine) is sending the data
* **Event Timestamp**: When the observation was made
* **Observation Type**: The metric we are measuring (e.g. Temperature, Pressure, Humidity...)
* **Observation Value**: The metric value

Once the table is created, then we need to start inserting data. Given that we don't have machines or sensors, we will simulate it.

We will create a new workflow in Apache NiFi with just two processors:

* **GenerateFlowFile**: With this Processor you can reate a new FlowFile with an arbitrary text and then schedule it so it can run every "x" seconds. You can create as many as you want to simulate different sensors.
  * **TIP**: In the "Custom Text" property you can directly create the insert statement (if you later use PutCassandraQL)
  * **TIP**: Since we don't have sensor data, consider using the [random function](https://nifi.apache.org/docs/nifi-docs/html/expression-language-guide.html#random) in NiFi for the values.
* **PutCassandraXX**: This one inserts into Cassandra. Feel free to either use PutCassandraQL or PutCassandraRecord.
  * **TIP**: you will need to add the "CassandraSessionProvider" pointing to the database ("cassandra:9042")

At the end, your NiFi workflow should look something like this, but be creative:

![Sensor Data NiFi Workflow](../../img/sensordata-nifi.png)

Now that we are inserting data, let's query it. In Apache Zeppelin, we are going to create a simple dashboard to visualize machine and sensor data.

Create new notebook, create a parametrized paragraph (you can select machine and sensor) which queries the table an collects the observations for the different metrics, visualizing it in a graph.

The notebook should look something like this, but also be creative:

![Sensor Data Zeppelin Notebook](../../img/sensordata-zeppelin.png)

### Deliverables

Once the exericise is done, you should have the following:

* Cassandra table(s) DDL(s)
* NiFi workflow
* Zeppelin dashboard

We will discuss in the class what we have built and why.