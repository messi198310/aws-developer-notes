A developer has been tasked with writing a new Lambda function that generates statistics from data stored in DynamoDB. 
The function must be able to be invoked both synchronous and asynchronously. 
Which of the following AWS services would use synchronous invocations to trigger the Lambda function?
    API Gateway
    Application Load Balancer

    API Gateway and Application Load Balancers both require Lambda functions to be invoked synchronously, as they require a response from the function before returning their own response to the user. S3 and SNS do not require a response from the Lambda function.

Protect a database on CloudFormation stack deletion 
    Set the DeletionPolicy to Retain in the CloudFormation template.

    The DeletionPolicy attribute can be used to preserve a specific resource when its stack is deleted. The DeletionPolicy Retain option can be used to ensure AWS CloudFormation keeps the resource without deleting the resource. The Stack Termination Protection feature enables protection against accidental deletion of an entire stack, not preservation of a specific resource. Similarly, the 'cloudformation:DeleteStack' Action applies to entire stack(s).

API to API Gateway formats 
    OpenAPI v3.0
    Swagger
    OpenAPI v2.0

    The Import API feature supports OpenAPI v2.0 and OpenAPI v3.0 definition files. Swagger is a common tool set that is originally defined the OpenAPI v2.0 specification. AWS use the name interchangeably with OpenAPI v2.0 . RAML is supported in a different tool (API Gateway Importer).

Making libraries available to lamdba 
    Upload the deployment package to Lambda
    Create a deployment package containing your function code and libraries
    Store the deployment package in an S3 bucket and then upload it to Lambda

    A deployment package is a ZIP archive that contains your function code and dependencies. You need to create a deployment package if you use the Lambda API to manage functions, or if you need to include libraries and dependencies other than the AWS SDK. You can upload the package directly to Lambda, or you can use an Amazon S3 bucket, and then upload it to Lambda. If the deployment package is larger than 50 MB, you must use Amazon S3.

Thousands of REST calls a minute - what service?
     API Gateway

     Questions containing 'REST' are usually related to APIs, so API Gateway looks the best answer. Elastic Beanstalk is a service which allows you to run applications without understanding the infrastructure and can be discounted, as can Global Accelerator which is a networking service that improves the availability and performance of applications. CloudFront can be used in conjunction with API Gateway to assist in geographically disparate calls, but won't process calls by itself.

DynamoDB write operation on a sequence of items, and roll back and reverse all operations in case of any one faulty operation - what is the best method?
    Use the TransactWriteItems operation

    DynamoDB transactions feature provides ability to group multiple items into a single atomic transaction and perform all-or-nothing coordinated operations. This can be done programmatically using the TransactWriteItems operation. The BatchWriteItem operation does not meet the question requirements as it does not guarantee that the actions will be performed on all items as a single atomic coordinated operation. It is possible that only some of the actions in the batch succeed while the others do not. Updating the payments application is not the ideal solution. It requires application code change and tracking all connected operations and reversing them as required is not trivial to implement. Using the native transaction ability provided by DynamoDB is a better option

GetItem operation is used to read data from a DynamoDB table. What strategy can be used to reduce the size of the read operations and increase read efficiency?
    Use Projection Expression.

    Projection Expressions are a DynamoDB feature used to limit the attributes returned by the GetItem operation. Thus, this can be used to reduce the size of the payload returned by a read operation. Parallel Scans allows multi-threaded applications to perform DynamoDB Scan operations quicker. It cannot be used with GetItem operations to make them more efficient. Pagination allows developer to perform a Scan operation on a table and divide the result set into multiple pages. It cannot be used to make GetItem operations more efficient. Filter expression can be used with Scan operations to filter the results returned by the scan operation. It is not a GetItem operation feature.

The Project Manager has asked you to roll out the updates as quickly as possible. Which of the following deployment strategies do you recommend?
    Rolling

    An all-at-once deployment deploys to all instances simultaneously which will put all of your web servers out of action at once. Rolling with additional batch launches an extra batch of instances before starting the deployment, to maintain full capacity. However, full capacity is not required in this scenario. Immutable deployments perform an immutable update to launch a full set of new instances running the new version of the application in a separate Auto Scaling group, alongside the instances running the old version; this is not required in this scenario. You can use a rolling update with a batch size of 25%, to ensure that 75% of your servers remain available at any time.

