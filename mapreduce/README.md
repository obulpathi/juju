MapReduce
=========

Bootstrap
---------
* juju bootstrap

Create master and cluster
-------------------------
* juju deploy hadoop master
* juju deploy hadoop cluster
* juju add-unit -n 2 cluster
* juju add-relation master:namenode cluster:datanode
* juju add-relation master:resourcemanager cluster:nodemanager

Initialize HDFS
---------------
* hdfs dfs -mkdir  /user/
* hdfs dfs -mkdir  /user/hadoop
* hdfs dfs -mkdir  /user/hadoop/input
* hdfs dfs -put gutenberg.txt /user/hadoop/input
* hdfs dfs -ls /user/hadoop/input

Run MapReduce programs
-----------------------
* tree /usr/local/hadoop
* ls /usr/local/hadoop/hadoop-2.2.0/share/hadoop/mapreduce/
* hadoop jar /usr/local/hadoop/hadoop-2.2.0/share/hadoop/mapreduce/hadoop-mapreduce-examples-2.2.0.jar wordcount /user/hadoop/input /user/hadoop/input
* hdfs dfs -ls /user/hadoop
* hdfs dfs -get /user/hadoop/* .

Destroy Environment
-------------------
* juju destroy-environment local
