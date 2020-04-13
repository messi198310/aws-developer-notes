A developer has been tasked with writing a new Lambda function that generates statistics from data stored in DynamoDB. 
The function must be able to be invoked both synchronous and asynchronously. 
Which of the following AWS services would use synchronous invocations to trigger the Lambda function?
   - API Gateway
   - Application Load Balancer

EXPLANATION - API Gateway and Application Load Balancers both require Lambda functions to be invoked synchronously, as they require a response from the function before returning their own response to the user. S3 and SNS do not require a response from the Lambda function.

----

Protect a database on CloudFormation stack deletion 
    - Set the DeletionPolicy to Retain in the CloudFormation template.

EXPLANATION - The DeletionPolicy attribute can be used to preserve a specific resource when its stack is deleted. The DeletionPolicy Retain option can be used to ensure AWS CloudFormation keeps the resource without deleting the resource. The Stack Termination Protection feature enables protection against accidental deletion of an entire stack, not preservation of a specific resource. Similarly, the 'cloudformation:DeleteStack' Action applies to entire stack(s).

----

API to API Gateway formats 
   - OpenAPI v3.0
   - Swagger
   - OpenAPI v2.0

EXPLANATION - The Import API feature supports OpenAPI v2.0 and OpenAPI v3.0 definition files. Swagger is a common tool set that is originally defined the OpenAPI v2.0 specification. AWS use the name interchangeably with OpenAPI v2.0 . RAML is supported in a different tool (API Gateway Importer).

----

Making libraries available to lamdba 
   - Upload the deployment package to Lambda
   - Create a deployment package containing your function code and libraries
   - Store the deployment package in an S3 bucket and then upload it to Lambda

EXPLANATION - A deployment package is a ZIP archive that contains your function code and dependencies. You need to create a deployment package if you use the Lambda API to manage functions, or if you need to include libraries and dependencies other than the AWS SDK. You can upload the package directly to Lambda, or you can use an Amazon S3 bucket, and then upload it to Lambda. If the deployment package is larger than 50 MB, you must use Amazon S3.

----

Thousands of REST calls a minute - what service?
    - API Gateway

EXPLANATION - Questions containing 'REST' are usually related to APIs, so API Gateway looks the best answer. Elastic Beanstalk is a service which allows you to run applications without understanding the infrastructure and can be discounted, as can Global Accelerator which is a networking service that improves the availability and performance of applications. CloudFront can be used in conjunction with API Gateway to assist in geographically disparate calls, but won't process calls by itself.

----

DynamoDB write operation on a sequence of items, and roll back and reverse all operations in case of any one faulty operation - what is the best method?
   - Use the TransactWriteItems operation

EXPLANATION - DynamoDB transactions feature provides ability to group multiple items into a single atomic transaction and perform all-or-nothing coordinated operations. This can be done programmatically using the TransactWriteItems operation. The BatchWriteItem operation does not meet the question requirements as it does not guarantee that the actions will be performed on all items as a single atomic coordinated operation. It is possible that only some of the actions in the batch succeed while the others do not. Updating the payments application is not the ideal solution. It requires application code change and tracking all connected operations and reversing them as required is not trivial to implement. Using the native transaction ability provided by DynamoDB is a better option

----

GetItem operation is used to read data from a DynamoDB table. What strategy can be used to reduce the size of the read operations and increase read efficiency?
   - Use Projection Expression.

EXPLANATION - Projection Expressions are a DynamoDB feature used to limit the attributes returned by the GetItem operation. Thus, this can be used to reduce the size of the payload returned by a read operation. Parallel Scans allows multi-threaded applications to perform DynamoDB Scan operations quicker. It cannot be used with GetItem operations to make them more efficient. Pagination allows developer to perform a Scan operation on a table and divide the result set into multiple pages. It cannot be used to make GetItem operations more efficient. Filter expression can be used with Scan operations to filter the results returned by the scan operation. It is not a GetItem operation feature.

----

The Project Manager has asked you to roll out the updates as quickly as possible. Which of the following deployment strategies do you recommend?
   - Rolling

EXPLANATION - An all-at-once deployment deploys to all instances simultaneously which will put all of your web servers out of action at once. Rolling with additional batch launches an extra batch of instances before starting the deployment, to maintain full capacity. However, full capacity is not required in this scenario. Immutable deployments perform an immutable update to launch a full set of new instances running the new version of the application in a separate Auto Scaling group, alongside the instances running the old version; this is not required in this scenario. You can use a rolling update with a batch size of 25%, to ensure that 75% of your servers remain available at any time.

----

What permissions need to be configured to allow CodeDeploy to perform the deployment to EC2?

   - Create an IAM policy with an acton to allow `codecommit:GitPull` on the required repository. Attach the policy to the EC2 instance profile role.
   
Explanation - CodeDeploy interacts with EC2 via the CodeDeploy Agent, which must be installed and running on the EC2 instance. During a deployment the CodeDeploy Agent running on EC2 pulls the source code from CodeCommit. The EC2 instance accesses CodeCommit using the permissions defined in its instance profile role; therefore, it is the EC2 instance itself that needs CodeCommit access. The specific CodeCommit permission needed to pull code is `codecommit:GitPull`.

----

You are developing a Lambda function which takes an average of 20 seconds to execute. During performance testing, you are trying to simulate peak loads, however soon after the testing begins, you notice that requests are failing with a throttling error. What could be the problem?

   - You have reached the limit of concurrent executions for Lambda.
   
Explanation - When requests come in faster than your function can scale, or when your function is at maximum concurrency, additional requests fail with a throttling error (429 status code).

----

An organization is considering performing canary deployments with their application. Which of the following statements best describes a canary deployment?

   - A new version of the application is deployed alongside the existing version. A proportion of application’s traffic is directed to the new application. If, after a given number of minutes, metrics demonstrate that the new version is performing correctly, the remainder of the traffic is moved to the new version.
   
Explanation - A canary deploy allows us to gain confidence in an application update by initially just releasing it to a subsection of users. Once we are satisfied that the update is working as expected, the update is then rolled out to the remaining users. The concept of a canary deployment is covered in the AWS Well-Architected Framework, and is a feature of API Gateway. It can also be performed manually using Route53 Weighted Records, or via an Application Load Balancer with a Forward Action and Weighted Target Groups.

----

You have configured your CI/CD process using CodePipeline, however you want to introduce a manual sign-off and approval process which needs to be completed before a new version of your application is deployed to Production. How can you achieve this?

   - Use the CodePipeline Manual Approvals feature
   
Explanation - With CodePipeline, you can add an approval action to a stage in a pipeline at the point where you want the pipeline execution to stop so that someone with the required AWS Identity and Access Management permissions can approve or reject the action.

----

You are developing a serverless retail application which includes a mobile app. All your product data is stored in DynamoDB, whilst the application itself runs on Lambda. The product catalogue is updated once every 6 months, to reflect seasonal stock and price updates. Each database read is 3KB in size and the application performs around 20 reads per second. Which of the following DynamoDB settings would you recommend?

   - Use eventually consistent reads
   - Configure the table with 10 read capacity units
   
Explanation - A read capacity unit represents one strongly consistent read per second, or two eventually consistent reads per second, for an item up to 4 KB in size. Eventually consistent reads provide greater throughput than strongly consistent. In this case the data changes infrequently, so eventually consistent is a good option.

----

You are working on a Serverless application written in Python and running in Lambda. You have uploaded multiple versions of your code to Lambda, but would like to make sure your test environment always utilizes the latest version. How can you configure this?

   - Reference the function using a qualified ARN and the $LATEST suffix
   - Reference the function using an unqualified ARN
   
Explanation - When you create a Lambda function, there is only one version: $LATEST. You can refer to the function using its Amazon Resource Name (ARN). There are two ARNs associated with this initial version, the qualified ARN which is the function ARN plus a version suffix e.g. $LATEST. Or the unqualified ARN which is the function ARN without the version suffix. The function version for an unqualified function always maps to $LATEST, so you can access the latest version using either the qualified ARN with $LATEST, or the unqualified function ARN. Lambda also supports creating aliases for each of your Lambda function versions. An alias is a pointer to a specific Lambda function version, aliases will not be updated automatically when a new version of the function becomes available.

----

You are planning to write some Python code which will query a DynamoDB table and display the output on your website, which of the following tools can you use to start writing your code?

   - Cloud9
   
Explanation - AWS Cloud9 is a cloud-based integrated development environment (IDE) that lets you write, run, and debug your code with just a browser. 

----

You work for a company which facilitates and organizes technical conferences. You ran a large number of events this year with many high profile speakers and would like to enable your customers to access videos of the most popular presentations. You have stored all your content in S3, but you would like to restrict access so that people can only access the videos after logging into your website. How should you configure this?

   - Remove public read access from the S3 bucket where the videos are stored
   - Share the videos by creating a pre-signed URL
   
Explanation - All objects by default are private. Only the object owner has permission to access these objects. However, the object owner can optionally share objects with others by creating a pre-signed URL, using their own security credentials, to grant time-limited permission to download the objects. Anyone who receives the pre-signed URL can then access the object. For example, if you have a video in your bucket and both the bucket and the object are private, you can share the video with others by generating a pre-signed URL.

----

You need to announce emergency downtime for a production AWS web application. This downtime notification requires different sets of instructions for different devices. All of the application users signed up to receive SNS notifications from the downtime topic when they began using the application and they are currently subscribed to this topic. What are appropriate ways for you to provide timely, device-specific instructions to end users when announcing this downtime?

   -  Send a single message, but customize the text in the SNS message field so that each device gets only the information that is appropriate for them.
   
Explanation - Using the SNS JSON message generator, you can choose the appropriate endpoint types and edit the generated code to send different text to the different endpoint types.

----

You are working on updates to your .NET application which has been deployed using Elastic Beanstalk. Your environment consists of 4 EC2 instances, as well as a number of different Lambda functions and DynamoDB tables. The application requires at least 2 instances to cope with the average workload and a minimum of 3 instances to cope with peak-time traffic. The Project Manager has asked you to roll out the updates as quickly as possible. Which of the following deployment strategies do you recommend?

   - Rolling
   
Explanation:
An all-at-once deployment deploys to all instances simultaneously which will put all of your web servers out of action at once. Rolling with additional batch launches an extra batch of instances before starting the deployment, to maintain full capacity. However, full capacity is not required in this scenario. Immutable deployments perform an immutable update to launch a full set of new instances running the new version of the application in a separate Auto Scaling group, alongside the instances running the old version; this is not required in this scenario. You can use a rolling update with a batch size of 25%, to ensure that 75% of your servers remain available at any time.

----

Your company uses Elastic Beanstalk to manage a web application. You were instructed to configure the Elastic Beanstalk environment's deployment policy to launch new EC2 instances, and then deploy the new version of your application only to these new resources.

Which of the following deployment methods can you use to meet this required configuration? (Select TWO)

   - Immutable
   - Bluie/Green deployment
 
Explanation

In ElasticBeanstalk, you can choose from a variety of deployment methods: 

- All at once – Deploy the new version to all instances simultaneously. All instances in your environment are out of service for a short time while the deployment occurs.

- Rolling – Deploy the new version in batches. Each batch is taken out of service during the deployment phase, reducing your environment's capacity by the number of instances in a batch.

- Rolling with additional batch – Deploy the new version in batches, but first launch a new batch of instances to ensure full capacity during the deployment process.

- Immutable – Deploy the new version to a fresh group of instances by performing an immutable update.

- Blue/Green - Deploy the new version to a separate environment, and then swap CNAMEs of the two environments to redirect traffic to the new version instantly.

---

A developer has deployed a Lambda function which will run in various environments such as DEV, TEST, UAT, and PROD. As part of its processing, the function also calls a set of external API services which varies based on the environment. The function must use different endpoints for these external services to properly complete the processing.

Which of the following features in Lambda should the developer use to reference the appropriate external endpoint for each environment?

   - Evironment Variables
   
Explanation

Environment variables for Lambda functions enable you to dynamically pass settings to your function code and libraries, without making changes to your code. Environment variables are key-value pairs that you create and modify as part of your function configuration, using either the AWS Lambda Console, the AWS Lambda CLI or the AWS Lambda SDK. AWS Lambda then makes these key-value pairs available to your Lambda function code using standard APIs supported by the language, like process.env for Node.js functions.

You can use environment variables to help libraries know what directory to install files in, where to store outputs, store connection and logging settings, and more. By separating these settings from the application logic, you don't need to update your function code when you need to change the function behavior based on different settings.

Stage Variables is incorrect because this is only available in API Gateway and not in Lambda.

Layers is incorrect because this feature is only used to pull in additional code and content in the form of layers. A layer is just a ZIP archive that contains libraries, a custom runtime, or other dependencies. 

Aliases is incorrect because this is just like a pointer to a specific Lambda function version. By using aliases, you can access the Lambda function which the alias is pointing to, without the caller knowing the specific version the alias is pointing to. 

---

A developer is working on an application which stores data to an Amazon DynamoDB table with the DynamoDB Streams feature enabled. He set up an event source mapping with DynamoDB Streams and AWS Lambda function to monitor any table changes then store the original data of the overwritten item in S3. When an item is updated, it should only send a copy of the item's previous value to an S3 bucket and maintain the new value in the DynamoDB table.

Which StreamViewType is the MOST suitable one to use in the DynamoDB configuration to fulfill this scenario?

   - OLD_IMAGE
   
Explanation

DynamoDB Streams provides a time-ordered sequence of item level changes in any DynamoDB table. The changes are de-duplicated and stored for 24 hours. Applications can access this log and view the data items as they appeared before and after they were modified, in near real time.



Amazon DynamoDB is also integrated with AWS Lambda so that you can create triggers—pieces of code that automatically respond to events in DynamoDB Streams. With triggers, you can build applications that react to data modifications in DynamoDB tables.

When an item in the table is modified, StreamViewType determines what information are written to the stream for this table. Valid values for StreamViewType are KEYS_ONLY, NEW_IMAGE, OLD_IMAGE, and NEW_AND_OLD_IMAGES.

For the OLD_IMAGE type, the entire item which has the previous value as it appeared before it was modified is written to the stream. Hence, this is the correct answer in this scenario.

KEYS_ONLY is incorrect because it will only write the key attributes of the modified item to the stream. This choice is wrong since the question states that values should be copied as well.

NEW_IMAGE is incorrect because it will configure the stream to write the entire item with its new value as it appears after it was modified. This choice is wrong since the stream should capture the item's pre-modified values.

NEW_AND_OLD_IMAGES is incorrect because although it writes the new values of the item in the stream, it also includes the old one as well. Since this type will send both the new and the old item images of the item to the stream, this option is wrong. Remember that it should only send a copy of the item's previous value to the S3 bucket, and not the new value in the DynamoDB table. The most suitable one to use here is the OLD_IMAGE type.

---

An application performs various workflows and processes long-running tasks that take a long time to complete. The users are complaining that the application is unresponsive since the workflow substantially increased the time it takes to complete a user request.

Which of the following is the BEST way to improve the performance of the application?

   - Use an Elastic Beanstalk worker environment to process the tasks aynchronously.
   
Explanation

If your application performs operations or workflows that take a long time to complete, you can offload those tasks to a dedicated worker environment. Decoupling your web application front end from a process that performs blocking operations is a common way to ensure that your application stays responsive under load.

A long-running task is anything that substantially increases the time it takes to complete a request, such as processing images or videos, sending email, or generating a ZIP archive. These operations can take only a second or two to complete, but a delay of a few seconds is a lot for a web request that would otherwise complete in less than 500 ms.

One option is to spawn a worker process locally, return success, and process the task asynchronously. This works if your instance can keep up with all of the tasks sent to it. Under high load, however, an instance can become overwhelmed with background tasks and become unresponsive to higher priority requests. If individual users can generate multiple tasks, the increase in load might not correspond to an increase in users, making it hard to scale out your web server tier effectively.

To avoid running long-running tasks locally, you can use the AWS SDK for your programming language to send them to an Amazon Simple Queue Service (Amazon SQS) queue, and run the process that performs them on a separate set of instances. You then design these worker instances to take items from the queue only when they have the capacity to run them, preventing them from becoming overwhelmed.

Elastic Beanstalk worker environments simplify this process by managing the Amazon SQS queue and running a daemon process on each instance that reads from the queue for you. When the daemon pulls an item from the queue, it sends an HTTP POST request locally to http://localhost/ on port 80 with the contents of the queue message in the body. All that your application needs to do is perform the long-running task in response to the POST. You can configure the daemon to post to a different path, use a MIME type other than application/JSON, connect to an existing queue, or customize connections (maximum concurrent requests), timeouts, and retries.

Hence, the best solution to meet the requirements of this scenario is to use an Elastic Beanstalk worker environment to process the tasks asynchronously.

Spawning a worker process locally in the EC2 instances then processing the tasks asynchronously is incorrect because although this is a valid solution, it is not scalable and hence, it's not the best one. Under high load, an instance can become overwhelmed with background tasks and become unresponsive to higher priority requests. This makes it hard to scale out your web server tier effectively.

Using a multicontainer docker environment in Elastic Beanstalk to process the long-running tasks asynchronously is incorrect because this is primarily used to support multiple containers per Amazon EC2 instance with multicontainer Docker platform. This is not applicable when processing long-running tasks and it is not scalable since it's not using an SQS queue.

Using an Amazon ECS Cluster with a Fargate launch type to process the tasks asynchronously is incorrect because Fargate just allows you to run your containerized applications without the need to provision and manage the backend infrastructure.

---

A developer is building a new Docker application using ECS. She needs to allow containers to access ports on the host container instance to send or receive traffic using port mapping.

Which component of ECS should the developer configure to properly implement this task?

   - Task Definition
  
Explanation  
Port mappings allow containers to access ports on the host container instance to send or receive traffic. Port mappings are specified as part of the container definition which can be configured in the task definition.

For task definitions that use the awsvpc network mode, you should only specify the containerPort. The hostPort can be left blank or it must be the same value as the containerPort.

Port mappings on Windows use the NetNAT gateway address rather than localhost. There is no loopback for port mappings on Windows, so you cannot access a container's mapped port from the host itself.

Hence, the correct component that the developer should configure is Task Definition.

Service scheduler is incorrect because this only provides you the ability to run tasks manually (for batch jobs or single run tasks), with Amazon ECS placing tasks on your cluster for you. The service scheduler is ideally suited for long running stateless services and applications but not to configure port mappings.

Container instance is incorrect because this is just an Amazon EC2 instance that is running the Amazon ECS container agent and has been registered into a cluster. When you run tasks with Amazon ECS, your tasks using the EC2 launch type are placed on your active container instances. However, you can't manually configure the port mappings directly on your container instances but through task definitions.

Container Agent is incorrect because this only allows container instances to connect to your cluster. The Amazon ECS container agent is included in the Amazon ECS-optimized AMIs, but you can also install it on any Amazon EC2 instance that supports the Amazon ECS specification. Same as the other incorrect options, you can't configure port mappings with this component.

---

A developer is building a web application which requires a multithreaded event-based key/value cache store that will cache result sets from database calls. You need to run large nodes with multiple cores for your cache layer and it should scale up or down as the demand on your system increases and decreases.

Which of the following is the MOST suitable service that you should use? 

   - Amaozon Elasticache for Memcached
   
Explanation

Redis and Memcached are popular, open-source, in-memory data stores. Although they are both easy to use and offer high performance, there are important differences to consider when choosing an engine. Memcached is designed for simplicity while Redis offers a rich set of features that make it effective for a wide range of use cases.

In this scenario, Redis can provide a much more durable and powerful cache layer to the prototype distributed system, however, you should take note of one keyword in the requirement: multithreaded. In terms of commands execution, Redis is mostly a single-threaded server. It is not designed to benefit from multiple CPU cores unlike Memcached, however, you can launch several Redis instances to scale out on several cores if needed.

Memcached is a more suitable choice since the scenario specifies that the system will run large nodes with multiple cores or threads which Memcached can adequately provide. 

You can choose Memcached over Redis if you have the following requirements:

- You need the simplest model possible.

- You need to run large nodes with multiple cores or threads.

- You need the ability to scale out and in, adding and removing nodes as demand on your system increases and decreases.

- You need to cache objects, such as a database.

This is why the most suitable answer to this scenario is Amazon ElastiCache for Memcached.

Amazon ElastiCache for Redis is incorrect because it does not totally support a multithreaded architecture, unlike Memcached. Although Redis has more features compared with Memcached, the scenario requires that the cache layer is multithreaded. This is why Memcached is a more suitable cache engine to choose from instead of Redis.

Amazon CloudFront is incorrect because it is primarily used as a Content Delivery Network (CDN) service which delivers your entire website, including dynamic, static, streaming, and interactive content using a global network of edge locations.

AWS IoT Greengrass is incorrect because this service is primarily used to enable connected devices to run AWS Lambda functions, execute predictions based on machine learning models, keep device data in sync, and communicate with other devices securely even without an Internet connection. Hence, this is not a suitable option for this scenario.

---

A developer has recently completed a new version of a serverless application that is ready to be deployed using AWS SAM. There is a requirement that the traffic should shift from the previous Lambda function to the new version gradually, in the shortest time possible. 

Which deployment configuration is the MOST suitable one to use in this scenario?

   - CodeDeployDefault.LambdaCanary10POercent5Minutes
   
Explanation

If you use AWS SAM to create your serverless application, it comes built-in with CodeDeploy to help ensure safe Lambda deployments. There are various deployment preference types that you can choose from.

For example:

If you choose Canary10Percent10Minutes then 10 percent of your customer traffic is immediately shifted to your new version. After 10 minutes, all traffic is shifted to the new version.

However, if your pre-hook/post-hook tests fail, or if a CloudWatch alarm is triggered, CodeDeploy rolls back your deployment. The following table outlines other traffic-shifting options that are available:

- Canary: Traffic is shifted in two increments. You can choose from predefined canary options. The options specify the percentage of traffic that's shifted to your updated Lambda function version in the first increment, and the interval, in minutes, before the remaining traffic is shifted in the second increment.

- Linear: Traffic is shifted in equal increments with an equal number of minutes between each increment. You can choose from predefined linear options that specify the percentage of traffic that's shifted in each increment and the number of minutes between each increment.

- All-at-once: All traffic is shifted from the original Lambda function to the updated Lambda function version at once.

Hence, the CodeDeployDefault.LambdaCanary10Percent5Minutes option is correct because 10 percent of your customer traffic is immediately shifted to your new version. After 5 minutes, all traffic is shifted to the new version. This means that the entire deployment time will only take 5 minutes

 

CodeDeployDefault.HalfAtATime is incorrect because this is only applicable for EC2/On-premises compute platform and not for Lambda.

CodeDeployDefault.LambdaLinear10PercentEvery1Minute is incorrect because it will add 10 percent of the traffic linearly to the new version every minute. Hence, all traffic will be shifted to the new version only after 10 minutes

CodeDeployDefault.LambdaLinear10PercentEvery2Minutes is incorrect because it will add 10 percent of the traffic linearly to the new version every 2 minutes. Hence, all traffic will be shifted to the new version only after 20 minutes.

 

