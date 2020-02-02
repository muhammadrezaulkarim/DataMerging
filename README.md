Execute in Windows 10 without Setting Up any Apache Spark Cluster:

Set up Hadoop for Windows:

1. Download the content of the entire folder in your local desktop/laptop

https://github.com/steveloughran/winutils/tree/master/hadoop-3.0.0

2. Copy the content in your destination directory. For example: C:\Users\UserX\hadoop-3.0.0

3. Set up Windows environment variables for Hadoop:

HADOOP_HOME: C:\Users\UserX\hadoop-3.0.0

Add the following entry in Windows environment variable path:

%HADOOP_HOME%\bin


Download Source Code:

1. Download the datamerging project in your local desktop/laptop:

git clone git@github.com:muhammadrezaulkarim/datamerging.git

Assume the project has been downloaded here: C:\Users\UserX\datamerging-master. UserX needs to be replaced by actual Windows user.


Run the program:

1. Open a Windows Command Prompt in administrative mode (Run as administrator). Move to the 'com.problemset.rezaul.datamerging' directory with the following command:

cd C:\Users\UserX\datamerging-master\com.problemset.rezaul.datamerging


2. Build the project in the command prompt:

mvn -U clean package

3. Execute the program in the command prompt:

java -jar target/datamerging-1.0.0-SNAPSHOT-jar-with-dependencies.jar local

The argument 'local' is required to run the program in local desktop/laptop without the need for setting up Apache Spark Cluster.

4. The output csv fill will be stored in the "data\output.csv" directory. 'service-guid' wise recoord count displayed on the command prompt.


Execute in Apache Spark Linux Cluster:

1. Build the project with Maven as described earlier

2. Copy the 'config' and 'data' directories from your project main directory to the 'target' directory

3. Copy the target directory to the master node of the Apache Spark Linux Cluster. Assume copied to the '/tmp' directory in the master node

4. Move to the target directory running the following command:

cd target

5. Submit the program to the Spark cluster with spark-submit command running the following command from the target directory:

/opt/spark/bin/spark-submit --verbose \
--class solutions.datamerging.DataMergingApp \
--master spark://spark-master:7077 \
/tmp/target/datamerging-1.0.0-SNAPSHOT-jar-with-dependencies.jar

You need to replace 'spark://spark-master:7077' with your Apache Spark Cluster Master node hostname. 

You might also have to replace the path for spark-submit command '/opt/spark/bin/spark-submit' depending on where it has been installed in the master node.


