Log of API calls from Lambda functions
    Enable CloudTrail for Lambda

    Enabling CloudTrail for Lambda will allow you to log all API calls to an S3 bucket.

Most efficient way to collect informatio on incoming and outgoing HTTP requests as well as latency in an application using Lambda, API Gateway, S3 and DynamoDB
    Use X-Ray to view the information, configure annotations to indicate which environment the traces relate. Group the data according to environment.

    AWS X-Ray is a service that collects data about requests that your application serves, and provides tools you can use to view, filter, and gain insights into that data to identify issues and opportunities for optimization. For any traced request to your application, you can see detailed information not only about the request and response, but also about calls that your application makes to downstream AWS resources, micro-services, databases and HTTP web APIs. When you instrument your application, the X-Ray SDK records information about incoming and outgoing requests, the AWS resources used, and the application itself. You can add other information to the segment document as annotations and metadata. Annotations are simple key-value pairs that are indexed for use with filter expressions. Use annotations to record data that you want to use to group traces in the console.

Lambda functions / API gateway endpoints and DynamoDB tables slowdown - where to check?
    AWS X-Ray helps developers analyze and debug production, distributed applications, such as those built using a micro-service architecture. With X-Ray, you can understand how your application and its underlying services are performing to identify and troubleshoot the root cause of performance issues and errors.

