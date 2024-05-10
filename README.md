# Spark-iceberg-minio
## OTPs
 
Open Table Formats (OTFs) are a phenomenon in the data analytics world that has been gaining momentum recently. The promise of OTFs is as a solution that leverages distributed computing and distributed object stores to provide capabilities that exceed what is possible with a Data Warehouse.  The open aspect of these formats gives organizations options when it comes to the choice of compute and storage. In theory, they could become a replacement for expensive Data Warehouses and overburdened Relational databases that have grown beyond their capabilities.


Apache Iceberg is one of three popular open table formats (OTF). The other two are Apache Hudi and Delta Lake. All three have impressive lineage - Iceberg came from Netflix, Uber originally developed Hudi, and Databricks designed Delta Lake. We also have similar tutorials for Hudi and Delta Lake: Building Streaming Data Lakes with Hudi and MinIO and Delta Lake and MinIO for Multi-Cloud Data Lakes.


In this post, I’ll introduce the Apache Iceberg table format. I’ll start by describing the Iceberg specification. From there, I’ll introduce an implementation of the Iceberg specification and show how to install it on a development in Window local.  Once we have a development machine setup, I’ll create a table, add data to it and walk through the three metadata levels of Apache Iceberg.
## What is Apache Iceberg?
Iceberg is a high-performance format for huge analytic tables. Iceberg brings the reliability and simplicity of SQL tables to big data, while making it possible for engines like Spark, Trino, Flink, Presto, Hive and Impala to safely work with the same tables, at the same time.

To implement the Apache Iceberg specification, we need three things:
   - A catalog to keep track of all the metadata files involved.
   - A processing engine that will behave like a query engine.
   - A high-speed, scalable storage solution for all the data files involved. (Ideally, the catalog uses object storage for metadata files as well - but this is not a requirement within the Apache Iceberg 
     specification.)


MinIO is the best object store for Iceberg - regardless of what you choose for a processing engine and a catalog. The files that make up the data and metadata of an Iceberg solution could be a bunch of small files, or they could be many very large files.

# Install Iceberg with hadoop catalog and minio

## Requirement
   - Java
   - Hadoop
   - Spark
   - Pyspark: `pip install pyspark==3.5.1

   ADD https://repo.maven.apache.org/maven2/org/apache/iceberg/iceberg-spark-runtime-3.3_2.12/1.1.0/iceberg-spark-runtime-3.3_2.12-1.1.0.jar $SPARK_HOME/jars

   
   ADD https://repo1.maven.org/maven2/org/apache/hadoop/hadoop-aws/3.3.4/hadoop-aws-3.3.4.jar $SPARK_HOME/jars

   
   ADD https://repo1.maven.org/maven2/org/apache/hadoop/hadoop-common/3.3.4/hadoop-common-3.3.4.jar $SPARK_HOME/jars

   
   ADD https://repo1.maven.org/maven2/com/amazonaws/aws-java-sdk-bundle/1.12.172/aws-java-sdk-bundle-1.12.172.jar $SPARK_HOME/jars

   
   ADD https://repo1.maven.org/maven2/software/amazon/awssdk/bundle/2.17.257/bundle-2.17.257.jar $SPARK_HOME/jars

   
   ADD https://repo1.maven.org/maven2/software/amazon/awssdk/url-connection-client/2.17.257/url-connection-client-2.17.257.jar $SPARK_HOME/jars

   
   ADD https://mvnrepository.com/artifact/org.apache.spark/spark-hadoop-cloud_2.12/3.3.4

