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

You have developed a CloudFormation stack in the AWS Management Console. You have a few small number of CloudFormation stacks saved in the Region in which you are operating in. When you launch your stack that contains many EC2 resources, you receive the error Status=start_failed. How would you troubleshoot this issue?

   - Use the Support Center in the AWS Management Console to request an increase in the number of EC2 instances.
   
Explanation - Verify that you didn't reach a resource limit. For example, the default number Amazon EC2 instances that you can launch is 20. If you try to create more Amazon EC2 instances than your account limit, the instance creation fails and you receive the error Status=start_failed. Also, during an update, if a resource is replaced, AWS CloudFormation creates new resource before it deletes the old one. This replacement might put your account over the resource limit, which would cause your update to fail. You can delete excess resources or request a limit increase. Saving the template in the CLI or waiting a few minutes will have no impact. The default limit for CloudFormation stacks is 200 and the question explicitly states that there are only a very small number of existing stacks.

Database queries are now running much slower than usual and the Operations Team are concerned that the DynamoDB table is being throttled. Which of the following approaches would you recommend to improve read performance?

   - Configure a DAX cluster and point the DynamoDB API calls at the DAX cluster
   
Explanation - Using DAX is the recommended approach to reducing response times for read-intensive applications, applications which read a small number of items frequently and also applications which perform repeated reads against a large set of data. Read Replicas are not a feature of DynamoDB. Configuring the application to use scans instead is not an efficient solution.

A developer deployed a serverless application consisting of an API Gateway and Lambda function using CloudFormation. Testing of the application resulted in a 500 status code and 'Execution failed due to configuration' error. What is a possible cause of the error?

   - POST method was not used when invoking the Lambda function from API Gateway.
   
Explanation - POST method must be used when invoking a Lambda function via REST API. This should not be confused with the methods used to access the APIs on the API Gateway. When deploying AWS Lambda and API Gateway resources via CloudFormation, you must ensure that the POST method is used when integrating API Gateway with an AWS Lambda function.

A company compliance policy mandates that all production account data must be stored across multiple geographically distant locations. In order to meet this requirement, they configured Amazon S3 Cross-Region Replication on their production account buckets. They find that S3 objects are not being replicated. What needs to be implemented to resolve this issue?

   - S3 source object owner must grant source bucket owner full access permissions.
   - Bucket policy on the destination bucket must allow the source bucket owner to replicate objects.
   
Explanation - S3 Bucket Versioning is a requirement to configure S3 Cross-Region Replication and must be enabled before S3 Cross-Region Replication can even be configured. This is therefore not part of the correct answer. S3 lifecycle policies are not related to replication of S3 data between accounts or regions. S3 lifecycle policies can be used to transition S3 objects to another Amazon S3 storage class. Using bucket event notifications would also not resolve this issue. Source bucket owner must have permissions to replicate objects on the destination S3 bucket in order for replication to succeed. This is accomplished by providing the source bucket owner permissions in the destination bucket policy. Additionally, source bucket owner must have access permissions to objects in the source bucket that are being replicated in order for replication to succeed. It is possible that IAM users other than the S3 bucket owner have permissions to put objects in the source bucket. In that scenario, the object owner must grant access permissions on the objects to the bucket owner.
