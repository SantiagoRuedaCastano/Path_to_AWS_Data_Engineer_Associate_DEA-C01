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
