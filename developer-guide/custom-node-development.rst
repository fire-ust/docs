Custom Node Development & Deployment
====================================

Fire Insights follows an open and extensible architecture allowing developers to add custom nodes that can be exposed in Fire UI and embedded into workflows.
 
 
**The details for building new nodes are available at the URL below:**
 
  * https://github.com/sparkflows/writing-new-node
  
**Examples of more complex nodes are at the URL below :**

  * https://github.com/sparkflows/sparkflows-stanfordcorenlp
 
Step 1: Start by cloning the github repo: writing-new-node
-----------------------------------------------------

The easiest way to start writing a new node or processor is by cloning the ``writing-new-node`` repo using the command below:

    git clone https://github.com/sparkflows/writing-new-node.git
  
Step 2: Install the Fire core jar to the local maven directory
-----------------------------------------------------
Install the fire core jar to your local maven repository. the pom.xml contains the dependency for it.
*mvn install:install-file -Dfile=fire-spark_2.4-core-3.1.0.jar -DgroupId=fire -DartifactId=fire-spark_2.4-core -Dversion=3.1.0 -Dpackaging=jar


Step 3: Code the new custom node
------------------------
The customer node might be a ``Dataset`` node or a ``Transform`` node.

A ``Dataset`` node reads data from some source into a Dataframe. It passes on this new Dataframe to the next node. Examples of data sources include:

    * Files on HDFS
    * HIVE tables
    * HBase tables
    * Cassandra
    * MongoDB
    * Salesforce / Marketo

A ``Transform`` node recieves an input Dataframe(s), transforms it and send the transformed Dataframe to the next node.

**Writing a Dataset node**
Create a new class that extends the ``NodeDataset`` class.

*Override the ``execute()`` method. The ``execute()`` method will read in data from the defined source into a Dataframe. It would the pass on the resulting DataFrame to the output node(s).
*Override the ``getOutputSchema()`` method to return the schema of the Dataframe created by the node.
 
**Writing a Transform node**
Create a new class that extends the ``Node`` class.
 
*Override the ``execute()`` method. The ``execute()`` method will ``transform`` the incoming Datafram and the pass on the resulting Dataframe to output node(s).
*If the node is updating the incoming schema, also override the ``getOutputSchema()`` methods. Otherwise the incoming schema to this node is sent to the next node(s).

**Examples of Custom Nodes**
Example of custom nodes are available at:

*https://github.com/sparkflows/writing-new-node/tree/master/src/main/java/fire/nodes/examples

 
Step 4: Create the node JSON file
-------------------------

Create the JSON file for the new node. The JSON file is used for displaying the new node in the ``Workflow Editor`` and capturing the user inputs of the various fields of the node through a ``Dialog box``. The JSON for the node also captures the name of the ``Java/Scala class`` which has the implementation code for the Node.

Fire supports various ``widgets types`` for capturing the details of the fields from the user through the ``Node Dialog Box``. 

**The details of the various widget types is available at the hyperkink below:**

* https://github.com/sparkflows/writing-new-node/blob/master/docs/README_Processor_JSON.md

**Examples of Node JSON:**

* https://github.com/sparkflows/writing-new-node/blob/master/testprintnrows.json
* https://github.com/sparkflows/sparkflows-stanfordcorenlp/tree/master/nodes/StanfordCoreNLP


Step 5: Deploy the Custom Node in the Fire Server
-----------------------------------------

Now that you have created a new node, follow the steps below to deploy it:
 
  * Create a jar file with ``mvn clean package``
  * Copy the jar file create above into ``fire-user-lib`` directory of Fire
  * Place the JSON file for the new node under the ``nodes`` directory.
  * ``Restart`` the Fire Server.
  * The new node will be picked up by the Fire Server and be visible in the ``Workflow Editor``
  * Check that new node is available as expected in the ``Workflow Editor``
  
Use the custom node in Spark submit when running on the Spark cluster
--------------------------------------------------------------------- 
 
  * Include the custom node with ``--jars <...>`` when running the workflow on the cluster


