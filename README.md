# Path to AWS Data Engineer Associate DEA-C01
The AWS Certified Data Engineer - Associate (DEA-C01)


[Exam guide](https://d1.awsstatic.com/training-and-certification/docs-data-engineer-associate/AWS-Certified-Data-Engineer-Associate_Exam-Guide.pdf)

# Exam Domain Breakdown
| Domain | Domain Weightings on Exams |
| :- | :- |
| Data Ingestion and Transformation | 34% |
| Data Store Management | 26% |
| Data Operations and Support | 22% |
| Data Security and Governance | 18% |


##### At most once
At most once means that a message will never be delivered more than one time. However, a message could be lost. Note that this pattern is only accepted when the data itself is low value or loses value if it is not immediately processed.

##### At least once
Delivery replays recent events starting from an acknowledged (known processed) event.  
This approach presents some data more than once to the processing pipeline. The typical implementation returns at-least-once delivery checkpoints to a safe point (so you know that they have been processed).

##### Exactly Once
This type of processing is the ideal because each event is processed exactly once. It avoids the difficult side effects and considerations raised by the other two deliveries. You can achieve exactly-once semantics using idempotency in combination with at-least-once delivery.



### Review operational characteristics of AWS ingestion services

|                                | Amazon DynamoDB Streams | Amazon Kinesis Data Stream (KDS) | Amazon Kinesis Data Firehose | Amazon MSK | Apache Kafka (on EC2) | Amazon SQS Standard | Amazon SQS FIFO |
|-------------------------------|--------------------------|-----------------------------------|-------------------------------|------------|------------------------|----------------------|------------------|
| **AWS Managed**               | Yes                      | Yes                               | Yes                           | Yes        | No                     | Yes                  | Yes              |
| **Use cases**                 | - Replication<br>- Mobile app<br>- Global multi-player game | Real-time data streaming       | Loader streaming data into data lakes, data stores and analytics tools | Real-time streaming data pipelines and applications | Real-time streaming data pipelines and applications | Queue               | Queue             |
| **Guaranteed ordering**       | Yes                      | Yes                               | No                            | Yes        | Yes                    | No                   | Yes              |
| **Delivery (deduping)**       | Exactly once             | At least once                     | At least once                 | At least once | At least once       | At least once        | Exactly once     |
| **Data retention period**     | 24 hours                 | 24 hours                          | N/A                           | Configurable | Configurable         | 14 days              | 14 days          |
| **Availability**              | 3 AZ                     | 3 AZ                              | 3 AZ                          | Configurable Multi AZ | Configurable Multi AZ | 3 AZ       |      3 AZ        |
| **Scale/throughput**          | No limit / Automatic     | No limit / Shards                 | No limit / Automatic          | Up to 30 / Brokers | No limit / Nodes     | No limit / Automatic | 300 TPS / Queue  |
| **Parallel Consumption**      | Yes                      | Yes                               | No                            | Yes        | Yes                    | No                   | No               |
| **Row/Object Size**           | 400 KB                   | 1 MB                              | Destination row / object size | Varies     | Varies                 | 256 KB               | 256 KB           |
| **Stream MapReduce**          | Yes                      | Yes                               | N/A                           | Yes        | Yes                    | N/A                  | N/A              |
| **Cost**                      | Higher                   | Low                               | Low                           | Low        | Low (+Admin)           | Low-Medium           | Low-Medium       |
