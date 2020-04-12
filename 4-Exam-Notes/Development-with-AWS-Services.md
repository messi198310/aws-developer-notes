A developer has been tasked with writing a new Lambda function that generates statistics from data stored in DynamoDB. 
The function must be able to be invoked both synchronous and asynchronously. 
Which of the following AWS services would use synchronous invocations to trigger the Lambda function?
   - API Gateway
   - Application Load Balancer

EXPLANATION - API Gateway and Application Load Balancers both require Lambda functions to be invoked synchronously, as they require a response from the function before returning their own response to the user. S3 and SNS do not require a response from the Lambda function.

Protect a database on CloudFormation stack deletion 
    - Set the DeletionPolicy to Retain in the CloudFormation template.

EXPLANATION - The DeletionPolicy attribute can be used to preserve a specific resource when its stack is deleted. The DeletionPolicy Retain option can be used to ensure AWS CloudFormation keeps the resource without deleting the resource. The Stack Termination Protection feature enables protection against accidental deletion of an entire stack, not preservation of a specific resource. Similarly, the 'cloudformation:DeleteStack' Action applies to entire stack(s).

API to API Gateway formats 
   - OpenAPI v3.0
   - Swagger
   - OpenAPI v2.0

EXPLANATION - The Import API feature supports OpenAPI v2.0 and OpenAPI v3.0 definition files. Swagger is a common tool set that is originally defined the OpenAPI v2.0 specification. AWS use the name interchangeably with OpenAPI v2.0 . RAML is supported in a different tool (API Gateway Importer).

Making libraries available to lamdba 
   - Upload the deployment package to Lambda
   - Create a deployment package containing your function code and libraries
   - Store the deployment package in an S3 bucket and then upload it to Lambda

EXPLANATION - A deployment package is a ZIP archive that contains your function code and dependencies. You need to create a deployment package if you use the Lambda API to manage functions, or if you need to include libraries and dependencies other than the AWS SDK. You can upload the package directly to Lambda, or you can use an Amazon S3 bucket, and then upload it to Lambda. If the deployment package is larger than 50 MB, you must use Amazon S3.

Thousands of REST calls a minute - what service?
    - API Gateway

EXPLANATION - Questions containing 'REST' are usually related to APIs, so API Gateway looks the best answer. Elastic Beanstalk is a service which allows you to run applications without understanding the infrastructure and can be discounted, as can Global Accelerator which is a networking service that improves the availability and performance of applications. CloudFront can be used in conjunction with API Gateway to assist in geographically disparate calls, but won't process calls by itself.

DynamoDB write operation on a sequence of items, and roll back and reverse all operations in case of any one faulty operation - what is the best method?
   - Use the TransactWriteItems operation

EXPLANATION - DynamoDB transactions feature provides ability to group multiple items into a single atomic transaction and perform all-or-nothing coordinated operations. This can be done programmatically using the TransactWriteItems operation. The BatchWriteItem operation does not meet the question requirements as it does not guarantee that the actions will be performed on all items as a single atomic coordinated operation. It is possible that only some of the actions in the batch succeed while the others do not. Updating the payments application is not the ideal solution. It requires application code change and tracking all connected operations and reversing them as required is not trivial to implement. Using the native transaction ability provided by DynamoDB is a better option

GetItem operation is used to read data from a DynamoDB table. What strategy can be used to reduce the size of the read operations and increase read efficiency?
   - Use Projection Expression.

EXPLANATION - Projection Expressions are a DynamoDB feature used to limit the attributes returned by the GetItem operation. Thus, this can be used to reduce the size of the payload returned by a read operation. Parallel Scans allows multi-threaded applications to perform DynamoDB Scan operations quicker. It cannot be used with GetItem operations to make them more efficient. Pagination allows developer to perform a Scan operation on a table and divide the result set into multiple pages. It cannot be used to make GetItem operations more efficient. Filter expression can be used with Scan operations to filter the results returned by the scan operation. It is not a GetItem operation feature.

The Project Manager has asked you to roll out the updates as quickly as possible. Which of the following deployment strategies do you recommend?
   - Rolling

EXPLANATION - An all-at-once deployment deploys to all instances simultaneously which will put all of your web servers out of action at once. Rolling with additional batch launches an extra batch of instances before starting the deployment, to maintain full capacity. However, full capacity is not required in this scenario. Immutable deployments perform an immutable update to launch a full set of new instances running the new version of the application in a separate Auto Scaling group, alongside the instances running the old version; this is not required in this scenario. You can use a rolling update with a batch size of 25%, to ensure that 75% of your servers remain available at any time.

What permissions need to be configured to allow CodeDeploy to perform the deployment to EC2?

   - Create an IAM policy with an acton to allow `codecommit:GitPull` on the required repository. Attach the policy to the EC2 instance profile role.
   
Explanation - CodeDeploy interacts with EC2 via the CodeDeploy Agent, which must be installed and running on the EC2 instance. During a deployment the CodeDeploy Agent running on EC2 pulls the source code from CodeCommit. The EC2 instance accesses CodeCommit using the permissions defined in its instance profile role; therefore, it is the EC2 instance itself that needs CodeCommit access. The specific CodeCommit permission needed to pull code is `codecommit:GitPull`.

You are developing a Lambda function which takes an average of 20 seconds to execute. During performance testing, you are trying to simulate peak loads, however soon after the testing begins, you notice that requests are failing with a throttling error. What could be the problem?

   - You have reached the limit of concurrent executions for Lambda.
   
Explanation - When requests come in faster than your function can scale, or when your function is at maximum concurrency, additional requests fail with a throttling error (429 status code).

An organization is considering performing canary deployments with their application. Which of the following statements best describes a canary deployment?

   - A new version of the application is deployed alongside the existing version. A proportion of application’s traffic is directed to the new application. If, after a given number of minutes, metrics demonstrate that the new version is performing correctly, the remainder of the traffic is moved to the new version.
   
Explanation - A canary deploy allows us to gain confidence in an application update by initially just releasing it to a subsection of users. Once we are satisfied that the update is working as expected, the update is then rolled out to the remaining users. The concept of a canary deployment is covered in the AWS Well-Architected Framework, and is a feature of API Gateway. It can also be performed manually using Route53 Weighted Records, or via an Application Load Balancer with a Forward Action and Weighted Target Groups.

You have configured your CI/CD process using CodePipeline, however you want to introduce a manual sign-off and approval process which needs to be completed before a new version of your application is deployed to Production. How can you achieve this?

   - Use the CodePipeline Manual Approvals feature
   
Explanation - With CodePipeline, you can add an approval action to a stage in a pipeline at the point where you want the pipeline execution to stop so that someone with the required AWS Identity and Access Management permissions can approve or reject the action.

You are developing a serverless retail application which includes a mobile app. All your product data is stored in DynamoDB, whilst the application itself runs on Lambda. The product catalogue is updated once every 6 months, to reflect seasonal stock and price updates. Each database read is 3KB in size and the application performs around 20 reads per second. Which of the following DynamoDB settings would you recommend?

   - Use eventually consistent reads
   - Configure the table with 10 read capacity units
   
Explanation - A read capacity unit represents one strongly consistent read per second, or two eventually consistent reads per second, for an item up to 4 KB in size. Eventually consistent reads provide greater throughput than strongly consistent. In this case the data changes infrequently, so eventually consistent is a good option.


You are working on a Serverless application written in Python and running in Lambda. You have uploaded multiple versions of your code to Lambda, but would like to make sure your test environment always utilizes the latest version. How can you configure this?

   - Reference the function using a qualified ARN and the $LATEST suffix
   - Reference the function using an unqualified ARN
   
Explanation - When you create a Lambda function, there is only one version: $LATEST. You can refer to the function using its Amazon Resource Name (ARN). There are two ARNs associated with this initial version, the qualified ARN which is the function ARN plus a version suffix e.g. $LATEST. Or the unqualified ARN which is the function ARN without the version suffix. The function version for an unqualified function always maps to $LATEST, so you can access the latest version using either the qualified ARN with $LATEST, or the unqualified function ARN. Lambda also supports creating aliases for each of your Lambda function versions. An alias is a pointer to a specific Lambda function version, aliases will not be updated automatically when a new version of the function becomes available.

You are planning to write some Python code which will query a DynamoDB table and display the output on your website, which of the following tools can you use to start writing your code?

   - Cloud9
   
Explanation - AWS Cloud9 is a cloud-based integrated development environment (IDE) that lets you write, run, and debug your code with just a browser. 
You work for a company which facilitates and organizes technical conferences. You ran a large number of events this year with many high profile speakers and would like to enable your customers to access videos of the most popular presentations. You have stored all your content in S3, but you would like to restrict access so that people can only access the videos after logging into your website. How should you configure this?

   - Remove public read access from the S3 bucket where the videos are stored
   - Share the videos by creating a pre-signed URL
   
Explanation - All objects by default are private. Only the object owner has permission to access these objects. However, the object owner can optionally share objects with others by creating a pre-signed URL, using their own security credentials, to grant time-limited permission to download the objects. Anyone who receives the pre-signed URL can then access the object. For example, if you have a video in your bucket and both the bucket and the object are private, you can share the video with others by generating a pre-signed URL.

You need to announce emergency downtime for a production AWS web application. This downtime notification requires different sets of instructions for different devices. All of the application users signed up to receive SNS notifications from the downtime topic when they began using the application and they are currently subscribed to this topic. What are appropriate ways for you to provide timely, device-specific instructions to end users when announcing this downtime?

   -  Send a single message, but customize the text in the SNS message field so that each device gets only the information that is appropriate for them.
   
Explanation - Using the SNS JSON message generator, you can choose the appropriate endpoint types and edit the generated code to send different text to the different endpoint types.

You are working on updates to your .NET application which has been deployed using Elastic Beanstalk. Your environment consists of 4 EC2 instances, as well as a number of different Lambda functions and DynamoDB tables. The application requires at least 2 instances to cope with the average workload and a minimum of 3 instances to cope with peak-time traffic. The Project Manager has asked you to roll out the updates as quickly as possible. Which of the following deployment strategies do you recommend?

   - Rolling
   
Explanation:
An all-at-once deployment deploys to all instances simultaneously which will put all of your web servers out of action at once. Rolling with additional batch launches an extra batch of instances before starting the deployment, to maintain full capacity. However, full capacity is not required in this scenario. Immutable deployments perform an immutable update to launch a full set of new instances running the new version of the application in a separate Auto Scaling group, alongside the instances running the old version; this is not required in this scenario. You can use a rolling update with a batch size of 25%, to ensure that 75% of your servers remain available at any time.

