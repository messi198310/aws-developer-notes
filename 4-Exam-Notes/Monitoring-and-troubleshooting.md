Log of API calls from Lambda functions
   - Enable CloudTrail for Lambda

EXPLANATION - Enabling CloudTrail for Lambda will allow you to log all API calls to an S3 bucket.

---

Most efficient way to collect information on incoming and outgoing HTTP requests as well as latency in an application using Lambda, API Gateway, S3 and DynamoDB
   - Use X-Ray to view the information, configure annotations to indicate which environment the traces relate. Group the data according to environment. (Also consider API Gateway Integration Latency metric in CloudWatch if an option)

EXPLANATION - AWS X-Ray is a service that collects data about requests that your application serves, and provides tools you can use to view, filter, and gain insights into that data to identify issues and opportunities for optimization. For any traced request to your application, you can see detailed information not only about the request and response, but also about calls that your application makes to downstream AWS resources, micro-services, databases and HTTP web APIs. When you instrument your application, the X-Ray SDK records information about incoming and outgoing requests, the AWS resources used, and the application itself. You can add other information to the segment document as annotations and metadata. Annotations are simple key-value pairs that are indexed for use with filter expressions. Use annotations to record data that you want to use to group traces in the console.

---

Lambda functions / API gateway endpoints and DynamoDB tables slowdown - where to check?
   - AWS X-Ray helps developers analyze and debug production, distributed applications, such as those built using a micro-service architecture. With X-Ray, you can understand how your application and its underlying services are performing to identify and troubleshoot the root cause of performance issues and errors.

---

Which of the following approaches will optimise the cost and performance of SQS?
   - Enable Long Polling
   
Explanation - In almost all cases, Amazon SQS long polling is preferable to short polling and results in higher performance and reduced cost in the majority of use cases.

---

Which service can the team use to collect information about traffic that is analyzed by the web ACLs in the AWS WAF logs?
   - Kinesis Data Firehose
   
Explanation - In order to enable and configure AWS WAF logs, a Kinesis Data Firehose is required for delivery of the logs to the destination.

---

You have developed a CloudFormation stack in the AWS Management Console. You have a few small number of CloudFormation stacks saved in the Region in which you are operating in. When you launch your stack that contains many EC2 resources, you receive the error Status=start_failed. How would you troubleshoot this issue?

   - Use the Support Center in the AWS Management Console to request an increase in the number of EC2 instances.
   
Explanation - Verify that you didn't reach a resource limit. For example, the default number Amazon EC2 instances that you can launch is 20. If you try to create more Amazon EC2 instances than your account limit, the instance creation fails and you receive the error Status=start_failed. Also, during an update, if a resource is replaced, AWS CloudFormation creates new resource before it deletes the old one. This replacement might put your account over the resource limit, which would cause your update to fail. You can delete excess resources or request a limit increase. Saving the template in the CLI or waiting a few minutes will have no impact. The default limit for CloudFormation stacks is 200 and the question explicitly states that there are only a very small number of existing stacks.

---

Database queries are now running much slower than usual and the Operations Team are concerned that the DynamoDB table is being throttled. Which of the following approaches would you recommend to improve read performance?

   - Configure a DAX cluster and point the DynamoDB API calls at the DAX cluster
   
Explanation - Using DAX is the recommended approach to reducing response times for read-intensive applications, applications which read a small number of items frequently and also applications which perform repeated reads against a large set of data. Read Replicas are not a feature of DynamoDB. Configuring the application to use scans instead is not an efficient solution.

---

A developer deployed a serverless application consisting of an API Gateway and Lambda function using CloudFormation. Testing of the application resulted in a 500 status code and 'Execution failed due to configuration' error. What is a possible cause of the error?

   - POST method was not used when invoking the Lambda function from API Gateway.
   
Explanation - POST method must be used when invoking a Lambda function via REST API. This should not be confused with the methods used to access the APIs on the API Gateway. When deploying AWS Lambda and API Gateway resources via CloudFormation, you must ensure that the POST method is used when integrating API Gateway with an AWS Lambda function.

---

A company compliance policy mandates that all production account data must be stored across multiple geographically distant locations. In order to meet this requirement, they configured Amazon S3 Cross-Region Replication on their production account buckets. They find that S3 objects are not being replicated. What needs to be implemented to resolve this issue?

   - S3 source object owner must grant source bucket owner full access permissions.
   - Bucket policy on the destination bucket must allow the source bucket owner to replicate objects.
   
Explanation - S3 Bucket Versioning is a requirement to configure S3 Cross-Region Replication and must be enabled before S3 Cross-Region Replication can even be configured. This is therefore not part of the correct answer. S3 lifecycle policies are not related to replication of S3 data between accounts or regions. S3 lifecycle policies can be used to transition S3 objects to another Amazon S3 storage class. Using bucket event notifications would also not resolve this issue. Source bucket owner must have permissions to replicate objects on the destination S3 bucket in order for replication to succeed. This is accomplished by providing the source bucket owner permissions in the destination bucket policy. Additionally, source bucket owner must have access permissions to objects in the source bucket that are being replicated in order for replication to succeed. It is possible that IAM users other than the S3 bucket owner have permissions to put objects in the source bucket. In that scenario, the object owner must grant access permissions on the objects to the bucket owner.

---

You are testing a new Serverless application which uses Lambda, S3, DynamoDB and API Gateway. You are suddenly seeing a large number of 4XX HTTP response codes coming from API Gateway. What could be the problem and what should you do about this?

   - This is a client error, you should fix the issue in your application and retry the request
   
Explanation - Client errors: Client errors are indicated by a 4xx HTTP response code. Client errors indicate that Amazon API Gateway found a problem with the client request, such as an authentication failure or missing required parameters. Fix the issue in the client application before submitting the request again. Server errors: Server errors are indicated by a 5xx HTTP response code, and need to be resolved by Amazon. You can resubmit/retry the request until it succeeds.

---

You are responsible for a number of different applications which are hosted across multiple regions. You would like to use CloudWatch to view all system metrics data in one place. Which of the following approaches should you choose?

   - Create a single dashboard to cover all the regions and include metrics for each application
   
Explanation - CloudWatch dashboards are customizable home pages in the CloudWatch console that you can use to monitor your resources in a single view, even those resources that are spread across different Regions.

---

Your application is running on EC2 and on Linux virtual machines in your own data center. You would like to configure your application to send data to X-Ray for troubleshooting and performance analysis. Which of the following steps will you need to complete?

   - Install the X-Ray SDK and the X-Ray daemon, then instrument your application to send data to X-Ray.
   
Explanation - You need the X-Ray SDK and the X-Ray daemon on your EC2 instances and on-premises systems, you then need to instrument your application to send the required data to X-Ray

---

You are attempting to list the objects contained in an S3 bucket. The bucket contains over 3000 objects and the list-objects command times out and does not complete successfully, however when you run the same command on a different bucket, it works without errors. What could be the reason for this?

   - You are running the command on a bucket which contains a large number of resources, and the default page size might be too high.
   
Explanation - If you see issues when running list commands on a large number of resources, the default page size of 1000 might be too high. This can cause calls to AWS services to exceed the maximum allowed time and generate a "timed out" error. You can use the --page-size option to specify that the AWS CLI request a smaller number of items from each call to the AWS service. The CLI still retrieves the full list, but performs a larger number of service API calls in the background and retrieves a smaller number of items with each call. This gives the individual calls a better chance of succeeding without a timeout. Changing the page size doesn't affect the output; it affects only the number of API calls that need to be made to generate the output.

---

A serverless application, which is composed of Lambda functions integrated with API Gateway and DynamoDB, processes ad hoc requests that are sent by its users. Due to the recent spike in incoming traffic, some of your customers are complaining that they are getting HTTP 504 errors from time to time.

Which of the following is the MOST likely cause of this issue?

   - API Gateway request has timed out becaise the underlying Lamba function has been running for more than 29 seconds.
   
Explanation

A gateway response is identified by a response type defined by API Gateway. The response consists of an HTTP status code, a set of additional headers that are specified by parameter mappings, and a payload that is generated by a non-VTL (Apache Velocity Template Language) mapping template.

You can set up a gateway response for a supported response type at the API level. Whenever API Gateway returns a response of the type, the header mappings and payload mapping templates defined in the gateway response are applied to return the mapped results to the API caller.

The following are the Gateway response types which are associated with the HTTP 504 error in API Gateway: 

INTEGRATION_FAILURE - The gateway response for an integration failed error. If the response type is unspecified, this response defaults to the DEFAULT_5XX type.

INTEGRATION_TIMEOUT - The gateway response for an integration timed out error. If the response type is unspecified, this response defaults to the DEFAULT_5XX type.

 

For the integration timeout, the range is from 50 milliseconds to 29 seconds for all integration types, including Lambda, Lambda proxy, HTTP, HTTP proxy, and AWS integrations.

In this scenario, there is an issue where the users are getting HTTP 504 errors in the serverless application. This means the Lambda function is working fine at times but there are instances when it throws an error. Based on this analysis, the most likely cause of the issue is the INTEGRATION_TIMEOUT error since you will only get an INTEGRATION_FAILURE error if your AWS Lambda integration does not work at all in the first place.

Hence, the root cause of this issue is that the API Gateway request has timed out because the underlying Lambda function has been running for more than 29 seconds. 

The option that says: "Since the incoming requests are increasing, the API Gateway automatically enabled throttling which caused the HTTP 504 errors." is incorrect because a large number of incoming requests will most likely produce an HTTP 502 or 429 error but not a 504 error. If executing the function would cause you to exceed a concurrency limit at either the account level (ConcurrentInvocationLimitExceeded) or function level (ReservedFunctionConcurrentInvocationLimitExceeded), Lambda may return a TooManyRequestsException as a response. For functions with a long timeout, your client might be disconnected during synchronous invocation while it waits for a response and returns an HTTP 504 error. 

The option that says: "An authorization failure occurred between API Gateway and the Lambda function." is incorrect because an authentication issue usually produces HTTP 403 errors and not 504s. The gateway response for authorization failures for missing authentication token error, invalid AWS signature error, or Amazon Cognito authentication problems is HTTP 403, which is why this option is unlikely to be the cause of this issue. 

The option that says: "The usage plan quota has been exceeded for the Lambda function" is incorrect because although this is a possible root cause for this scenario, this option has the least chance to produce HTTP 504 errors. The scenario says that the issue happens from time to time and not all the time which suggests that this happens intermittently. If the usage plan indeed exceeded the quota, then the 504 error should always show up and not just from time to time.

---

A mission-critical application is required to have a monitoring system which can provide immediate insight into its sub-minute activity. You are required to collect the data of all of the users who are currently logged in to the system every 10 seconds. 

Which of the following options is the MOST suitable solution that you should do to meet the above requirements?

   - Publish a high-resolution custom metric to CloudWatch.
   
You can publish your own metrics to CloudWatch using the AWS CLI or an API. You can view statistical graphs of your published metrics with the AWS Management Console. CloudWatch stores data about a metric as a series of data points. Each data point has an associated time stamp. You can even publish an aggregated set of data points called a statistic set.

Each metric is one of the following:

    - Standard resolution, with data having a one-minute granularity

    - High resolution, with data at a granularity of one second

 

Metrics produced by AWS services are standard resolution by default. When you publish a custom metric, you can define it as either standard resolution or high resolution. When you publish a high-resolution metric, CloudWatch stores it with a resolution of 1 second, and you can read and retrieve it with a period of 1 second, 5 seconds, 10 seconds, 30 seconds, or any multiple of 60 seconds.

High-resolution metrics can give you more immediate insight into your application's sub-minute activity. Keep in mind that every PutMetricData call for a custom metric is charged, so calling PutMetricData more often on a high-resolution metric can lead to higher charges. 

Therefore, the correct answer in this scenario is to publish a high-resolution custom metric to CloudWatch.

The option that says: "Publish a custom metric to CloudWatch using the PutMetricData API with the --storage-resolution parameter set to its default value" is incorrect because the default value of the --storage-resolution parameter is 60, which stores data in one-minute granularity. This parameter should be set to 1 in order to configure it as a high-resolution metric.

The option that says: "Enable detailed monitoring" is incorrect because it will only store metric data in one-minute granularity. Moreover, you have to publish a custom metric for this scenario since the type of data that you have to monitor is specific only to your application.

The option that says: "Enable enhanced monitoring" is incorrect because this type of monitoring is primarily used only in RDS.

---

A recently deployed Lambda function has an intermittent issue in processing customer data. You enabled the active tracing option in order to detect, analyze, and optimize performance issues of your function using the X-Ray service.

Which of the following environment variables are used by AWS Lambda to facilitate communication with X-Ray? (Select TWO)

   - AWS_XRAY_CONTEXT_MISSING
   - _X_AMZN_TRACE_ID
   
Explanation

AWS X-Ray is an AWS service that allows you to detect, analyze, and optimize performance issues with your AWS Lambda applications. X-Ray collects metadata from the Lambda service and any upstream or downstream services that make up your application. X-Ray uses this metadata to generate a detailed service graph that illustrates performance bottlenecks, latency spikes, and other issues that impact the performance of your Lambda application.

AWS Lambda uses environment variables to facilitate communication with the X-Ray daemon and configure the X-Ray SDK.

_X_AMZN_TRACE_ID: Contains the tracing header, which includes the sampling decision, trace ID, and parent segment ID. If Lambda receives a tracing header when your function is invoked, that header will be used to populate the _X_AMZN_TRACE_ID environment variable. If a tracing header was not received, Lambda will generate one for you.

AWS_XRAY_CONTEXT_MISSING: The X-Ray SDK uses this variable to determine its behavior in the event that your function tries to record X-Ray data, but a tracing header is not available. Lambda sets this value to LOG_ERROR by default.

AWS_XRAY_DAEMON_ADDRESS: This environment variable exposes the X-Ray daemon's address in the following format: IP_ADDRESS:PORT. You can use the X-Ray daemon's address to send trace data to the X-Ray daemon directly, without using the X-Ray SDK.

Therefore, the correct answers for this scenario are the _X_AMZN_TRACE_ID and AWS_XRAY_CONTEXT_MISSING environment variables.

AWS_XRAY_TRACING_NAME is incorrect because this is primarily used in X-Ray SDK where you can set a service name that the SDK uses for segments.

AWS_XRAY_DEBUG_MODE is incorrect because this is used to configure the SDK to output logs to the console without using a logging library.

AUTO_INSTRUMENT is incorrect because this is primarily used in X-Ray SDK for Django Framework only. This allows the recording of subsegments for built-in database and template rendering operations. 

---

