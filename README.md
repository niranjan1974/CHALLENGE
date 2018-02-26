# CHALLENGE
Problem Statement
The problem is to compute Top 10 most frequent routes within the last 30 minutes of streaming data. A route is represented by a starting grid cell and an ending grid cell. The data is sorted chronologically according to the dropoff_datetime. The output results must be updated whenever any of the 10 most frequent routes changes. The output format for the result stream is:
pickup_datetime, dropoff_datetime, start_cell_id_1, end_cell_id_1, ... , start_cell_id_10, end_cell_id_10, delay
where pickup_datetime, dropoff_datetime are the timestamps of the trip report that resulted in an update of the result stream, start_cell_id_X the starting cell of the Xth-most frequent route, end_cell_id_X the ending cell of the Xth-most frequent route. If less than 10 routes can be identified within the last 30 min, then NULL is to be output for all routes that lack data.
The attribute delay captures the time delay between reading the input event that triggered the output and the time when the output is produced. Participants must determine the delay using the current system time right after reading the input and right before writing the output. This attribute will be used in the evaluation of the submission.


Data Ingestion:

Data from source is ingested into Kafka topics using Kafka Producer which allows to publish records to the Kafka topics synchronously and asynchronously.
Producer logic to pull the data from source systems and ingest into Kafka topic.

Stream Processing :

Kafka consumer consumes the data from topics and streams using Spark streaming logic written using pyspark.

Hive :

Create EXTERNAL HIVE TABLE on top of the Sequence Files to make data available and add partitions to the table to optimize query performance

PowerBI Dashboards:

Connected Power BI to Hive.
