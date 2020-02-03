
A. Why Apache Spark and Maven?

Apache Spark is an open source distributed cluster-computing framework for processing big data. It is a unified analytics engine for big data and supports batch and stream data processing, machine learning and distributed graph processing. 

Even though the given csv, xml and json data sets are very small, Apache Spark has been used considering its abilty to process data of any size.

Maven is a widely used build automation tool.

B. Execute in Windows 10 without Setting Up any Apache Spark Cluster:

Set up Hadoop for Windows Binaries:

1. Download the content of the entire folder in your local desktop/laptop from GitHub (Link: https://github.com/steveloughran/winutils/tree/master/hadoop-3.0.0):

Following command can aslo be used to download with git tool:

git clone https://github.com/steveloughran/winutils.git


2. Copy the content in your destination directory. For example: C:\Users\UserX\hadoop-3.0.0

'UserX' needs to be replaced with actual Windows user name.

3. Set up a Windows environment variable for Hadoop:

variable name: HADOOP_HOME

variable value: C:\Users\UserX\hadoop-3.0.0

Add the following entry in Windows system variable path:

%HADOOP_HOME%\bin


Download Source Code:

1. Download the 'datamerging' project in your local desktop/laptop running the following command:

git clone git@github.com:muhammadrezaulkarim/datamerging.git

Assume the project has been downloaded here: 'C:\Users\UserX\datamerging-master'. 'UserX' needs to be replaced with actual Windows user.


Build and Execute the Program:

1. Open a Windows Command Prompt in administrative mode (Run as administrator). Move to the 'com.problemset.rezaul.datamerging' directory with the following command:

cd C:\Users\UserX\datamerging-master\com.problemset.rezaul.datamerging


2. Build the project in the command prompt:

mvn -U clean package

3. Execute the program in the command prompt:

java -jar target/datamerging-1.0.0-SNAPSHOT-jar-with-dependencies.jar local

The argument 'local' is required to run the program in local desktop/laptop without the need for setting up Apache Spark Cluster. Java 8 is a pre-requisite for this project. Java can be downloaded from this Link: https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html

4. The output csv file will be stored in the "data\output.csv" directory within the project. 'service-guid' wise record count will be displayed on the command prompt


C. Execute in Apache Spark Linux Cluster (Optional):

1. Build the project with Maven as described earlier

2. Copy the 'config' and 'data' directories from your project main directory to the 'target' directory

3. Copy the target directory to the master node of the Apache Spark Linux Cluster. Assume copied to the '/tmp' directory in the master node

4. Move to the target directory running the following command:

cd target

5. Submit the program to the Spark cluster with 'spark-submit' running the following command from the '/tmp/target' directory:

/opt/spark/bin/spark-submit --verbose --class solutions.datamerging.DataMergingApp --master spark://spark-master:7077 /tmp/target/datamerging-1.0.0-SNAPSHOT-jar-with-dependencies.jar

You need to replace 'spark://spark-master:7077' with your Apache Spark Cluster Master node hostname. 

You might also have to replace the path for spark-submit command '/opt/spark/bin/spark-submit' depending on where it has been installed in the master node.


D. Execute in Apache Spark on Amazon EMR (Cloud):

If you already have a Apache Spark Cluster in Amazon EMR, you can also use spark-submit to execute the program.


E. Set Up Maven in Windows 10:

1. Download Apache Maven from here:

https://www-eu.apache.org/dist/maven/maven-3/3.6.3/binaries/apache-maven-3.6.3-bin.zip

2. Unzip and place the 'apache-maven-3.6.3' directory here:

C:\Users\UserX\apache-maven-3.6.3

'UserX' needs to be replaced with actual Windows user name.

3. Set up a Windows environment variable for Maven:

variable name: MAVEN_HOME

variable value: C:\Users\UserX\apache-maven-3.6.3

Add the following entry in Windows system variable path:

%MAVEN_HOME%\bin


F. Sample Output:

1. service-guid wise record count:   

+------------------------------------+-----+
|service-guid                        |count|
+------------------------------------+-----+
|0342f6df-6e8c-48c3-8390-667eb678638b|12   |
|0a5f0733-d058-4738-8666-f0468c5ee9c3|20   |
|0d5157f7-8012-4455-b66f-4f81d14092b3|18   |
|0ee908d7-d767-4da5-9cbe-fc78e9c6a192|10   |
|147fe620-dd62-4eb6-9a0d-8b8ca1e743b1|20   |
|1664d39d-45f1-4939-87e2-b7221e30d157|13   |
|185ec7fa-2efc-424e-835f-de882857f55e|9    |
|19f26076-5d21-4200-b26c-0f32cd87ebde|14   |
|1d0a29e3-b3b0-4f0d-a684-a0f025955a4d|11   |
|1efced85-b0e3-464b-ac63-472d35909c05|14   |
|2536e29e-3570-4d53-be7c-b9d059c632a7|12   |
|26ea4cf2-ed09-43d4-a8e6-e3ff1f8e5893|18   |
|318e9d5d-53f9-43eb-a9d1-88b5c51687f8|15   |
|35501e3f-e06c-4cb5-9062-e8611a591cab|14   |
|3cc76b74-7d16-4651-9699-34332a56f6e7|15   |
|3fb4c246-cf94-4f60-bf47-b709b288f9b2|13   |
|4a949998-0e79-4ec1-9894-11360712fc45|12   |
|4ab70dbe-f5e7-4688-aa5c-2ae75faf6c03|17   |
|4cb309f6-8c9a-4f61-8544-6b458e42f04c|16   |
|50b89ee3-f4cb-46d9-8d5c-319f6a032406|9    |
|52073b51-cd51-4438-bd54-3bce3a7c239f|19   |
|586b3947-c63c-4054-a437-d3f8a6836bcf|17   |
|5d35c640-9cf3-43ec-ae1a-5feebed26a37|15   |
|601152f5-477a-4ff3-afdb-8bf315341254|23   |
|60b84364-645b-444c-90ed-879d893f7920|17   |
|6c7444d3-9bca-46d7-a8c6-96939981ae01|12   |
|7d619a45-2b4d-4a54-9e85-6913c9545e34|17   |
|7f386bb2-4bbf-4f14-b56e-3dad78f28674|11   |
|8105e514-c0d5-40ba-8c7a-90bf998ba9e4|21   |
|8151ff61-4777-4187-b719-e750b91281c8|18   |
|8232ac92-6020-4101-88c0-74d51ea1542b|14   |
|8de44210-f265-4f16-a94b-8b0eadc0de23|15   |
|90e5b65b-4f12-4bb2-9554-3f5969f4d78b|14   |
|92aa1c5c-98ab-49f8-a427-4c0bc49d6872|18   |
|94f93cba-de8c-4fb6-a03c-d52c10f81247|12   |
|98279a79-c822-45b4-8429-45ce97a336e5|20   |
|9e3d54d8-bcea-4bd5-94f5-bd636df152fa|17   |
|a5adb83b-0380-4618-aef6-7179e39eff26|6    |
|a6c5d611-45be-43bf-a027-c1e98a89c8f6|14   |
|a944a262-6fdb-4f7f-a510-d123ed9618e6|14   |
|b3be9c1c-5712-420d-a359-e9ef0e93c9c5|22   |
|b8cf6fd8-06e2-4e5b-8ed6-6efc8e0ecda3|21   |
|bed314cb-4c59-41ee-9c23-3155a80e2bc3|18   |
|c5a5edbb-338d-449a-99cb-1baeba48abb2|12   |
|caaca31e-bee2-4ed3-8e72-5dab24079744|14   |
|d15e4790-67f7-4488-a28d-32ced8673c58|18   |
|d224de85-cd41-4f03-bff6-de9815877975|14   |
|d70c87de-7837-450c-9965-17c9f366d183|19   |
|d7d6b499-509a-4c08-b95e-68d9662f25ca|9    |
|db7b9cde-0a4b-459a-a301-88a447410499|17   |
|dc81cacc-af4f-4b0a-8a10-34e106ffdf23|12   |
|dd7691ef-4b29-4992-b48d-cb449dfc65b6|15   |
|e16b762f-d0a2-4e1f-95a2-2ee9985c6aff|11   |
|e49b6654-fca2-47b2-b816-4bb7e09c6fa3|14   |
|edf32a15-bb1c-42f4-9fe6-afa9f9b21522|8    |
|ef48c441-4a26-4f90-97cf-cc3d0665b814|9    |
|f78fb4fb-3e02-4f42-9c15-45480342cba9|11   |
|fa005302-61ce-44ca-88a5-015fd4392f37|15   |
|fa7b1137-1e85-4d26-aa9d-8da7a812cad6|18   |
|fbce0713-676d-4dc9-a33b-25ff937c1ae3|11   |
+------------------------------------+-----+

2. Output CSV file:
https://github.com/muhammadrezaulkarim/datamerging/blob/master/com.problemset.rezaul.datamerging/data/output.csv/part-00000-9f4adc11-1ecf-4bb3-8c19-95fd0cafc155-c000.csv
