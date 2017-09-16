# Run_Higher_Spark_Version_Cluster_with_lower-version
This project is just the readme on how to run higher spark version on cluster with lower spark version

# Command to execute higher Apache spark version on cluster with Lower Spark version 

In this example we have hortonworks cluster with Apache spark 1.5 version however we had a requirement to use 
Apache Spark version 1.6 due to new functionalities in the same .

please follwow below command, this command should be executed with the machine having access to cluster may be ideally edge node

spark-submit --master yarn_cluster --driver-class-path spark-assembly-1.6.0-hadoop2.6.0.jar --conf spark.executor.userClassPathFirst=true --conf spark.executor.extraClassPath=tmp/spark-assembly-1.6.0-hadoop2.6.0.jar --class com.foo.Main target/scala-2.10/com.foo.application.jar

* --driver-class-path spark-assembly-1.6.0-hadoop2.6.0.jar so the driver start with spark 1.6 version 
* spark.executor.extraClassPath=<hdfs path to spark assembly jar> since it will be then used by spark executors 
* spark.executor.userClassPathFirst=true  this make dure that when the executer are running the application they refer to the spark 1.6 latest version 
