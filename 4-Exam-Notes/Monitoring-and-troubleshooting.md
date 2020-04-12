Log of API calls from Lambda functions
   - Enable CloudTrail for Lambda

EXPLANATION - Enabling CloudTrail for Lambda will allow you to log all API calls to an S3 bucket.

Most efficient way to collect information on incoming and outgoing HTTP requests as well as latency in an application using Lambda, API Gateway, S3 and DynamoDB
   - Use X-Ray to view the information, configure annotations to indicate which environment the traces relate. Group the data according to environment. (Also consider API Gateway Integration Latency metric in CloudWatch if an option)

EXPLANATION - AWS X-Ray is a service that collects data about requests that your application serves, and provides tools you can use to view, filter, and gain insights into that data to identify issues and opportunities for optimization. For any traced request to your application, you can see detailed information not only about the request and response, but also about calls that your application makes to downstream AWS resources, micro-services, databases and HTTP web APIs. When you instrument your application, the X-Ray SDK records information about incoming and outgoing requests, the AWS resources used, and the application itself. You can add other information to the segment document as annotations and metadata. Annotations are simple key-value pairs that are indexed for use with filter expressions. Use annotations to record data that you want to use to group traces in the console.

Lambda functions / API gateway endpoints and DynamoDB tables slowdown - where to check?
   - AWS X-Ray helps developers analyze and debug production, distributed applications, such as those built using a micro-service architecture. With X-Ray, you can understand how your application and its underlying services are performing to identify and troubleshoot the root cause of performance issues and errors.

Which of the following approaches will optimise the cost and performance of SQS?
   - Enable Long Polling
   
Explanation - In almost all cases, Amazon SQS long polling is preferable to short polling and results in higher performance and reduced cost in the majority of use cases.

Which service can the team use to collect information about traffic that is analyzed by the web ACLs in the AWS WAF logs?
   - Kinesis Data Firehose
   
Explanation - In order to enable and configure AWS WAF logs, a Kinesis Data Firehose is required for delivery of the logs to the destination.
