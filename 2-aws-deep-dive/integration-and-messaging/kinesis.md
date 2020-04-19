Kinesis

Kinesis is composed of stream, firehose and analytics components.

Kinesis Data Streams - Amazon Kinesis Data Streams is a scalable and durable real-time data streaming service that can continuously capture gigabytes of data per second from hundreds of thousands of sources.

Kinesis Firehose - Amazon Kinesis Data Firehose is the easiest way to capture, transform, and load data streams into AWS data stores for near real-time analytics with existing business intelligence tools.

Kinesis Analytics - Amazon Kinesis Data Analytics is the easiest way to process data streams in real time with SQL or Java without having to learn new programming languages or processing frameworks.
Kinesis Data Streams

    A data stream represents a group of data records. The data records in a data stream are distributed into shards.

    A shard has a sequence of data records in a stream.

    Records are ordered per shard basis.

    Partition key is used to segregate and route records to different shards of a data stream. A partition key is specified by your data producer while adding data to an Amazon Kinesis data stream.

  	 
Data retention period 	            24 hours - 7 days
Maximum size of a data blob 	      1 MB
Shard data input capacity 	        1 MB/sec
Shard data output capacity 	        2 MB/sec

Writing Data
Kinesis Producer Library

Kinesis Producer Library (KPL) simplifies producer application development, allowing developers to achieve high write throughput to a Kinesis data stream.

KPL performs these tasks to achieve high write throughput to a kinesis stream.

    Writes to one or more Kinesis data streams with an automatic and configurable retry mechanism

    Collects records and uses PutRecords to write multiple records to multiple shards per request

    Aggregates user records to increase payload size and improve throughput

    Integrates seamlessly with the Kinesis Client Library (KCL) to de-aggregate batched records on the consumer

    Submits Amazon CloudWatch metrics on your behalf to provide visibility into producer performance

Reading Data
Kinesis Client Library

The Kinesis Client Library (KCL) helps you consume and process data from a Kinesis data stream.

The KCL takes care of many of the complex tasks associated with distributed computing, such as load balancing across multiple instances, responding to instance failures, checkpointing processed records, and reacting to resharding.

    Each shard can be read by only one KCL instance.

    For each Amazon Kinesis Data Streams application, the KCL uses a unique Amazon DynamoDB table to keep track of the application’s state.

    Kinesis Client Library (KCL) delivers all records for a given partition key to the same record processor, making it easier to build multiple applications reading from the same Amazon Kinesis data stream (for example, to perform counting, aggregation, and filtering)
