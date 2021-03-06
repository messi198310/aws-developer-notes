DynamoDB

-In DynamoDB, a primary key can be composite partition/sort key.

-In DynamoDB, a primary key can be a single-attribute partition key

----

Message sending from ECS - What policy?
   - The policy must be attached to the ECS Task's execution role to allow the application running in the container access SQS.

----

Best practices for instances
   - Reserved instances provide a significant discount compared to running instances On-Demand. You can take advantage of Spot Instances 
    to run and scale applications such as stateless web services, image rendering, big data analytics, 
    and massively parallel computations. Dedicated Instances are Amazon EC2 instances that run in a VPC on hardware that is dedicated to a single customer.

----

Increasing performance of EBS Volumes
   - Schedule snapshots of HDD based volumes for periods of low use
   - Stripe volumes together in a RAID 0 configuration.
   - Ensure that your EC2 instances are types that can be optimized for use with EBS

----

Services to build with from Elastic Beanstalk
   - Auto Scaling Group
   - Elastic Load Balancer
   - EC2
   - S3
   
EXPLANATION - Except for Lambda, all of the services listed can be used to create a web server farm. 
      AWS Lambda automatically runs your code without requiring you to provision or manage servers. 
      Lambda is generally used for stateless, short-running tasks and is not suitable for long-running tasks like running a web server.

----

Docker commands to push image
   - Run: aws ecr get-login --no-include-email --region us-east-1 Run the docker login command that was returned in the previous step. Then run: docker push 123456789012.dkr.ecr.us-east-1.amazonaws.com/my-repository
   - Run: docker tag -i my-image latest Then run: docker push 123456789012.dkr.ecr.us-east-1.amazonaws.com/my-repository

EXPLANATION - The aws ecr get-login command provides an authorization token that is valid for 12 hours. You need to run the command which was returned by the ecr get-login command to authorize you to push images to the ECR repository. For a full list of the steps, see the link below.

----

Which of the following AWS services could the organization use under this new serverless policy?
   - Fargate
   - S3
   - DynamoDB

EXPLANATION - AWS consider S3, DynamoDB, and Fargate to be serverless services.

----

What is the AWS recommended way of managing large messages in SQS?
   - Store the messages using S3
   - Use the Amazon SQS Extended Client Library for Java to manage SQS messages
   
Explanation - You can use Amazon S3 and the Amazon SQS Extended Client Library for Java to manage Amazon SQS messages. This is especially useful for storing and consuming messages up to 2 GB in size. Unless your application requires repeatedly creating queues and leaving them inactive or storing large amounts of data in your queue, consider using Amazon S3 for storing your data. You can use the Amazon SQS Extended Client Library for Java to manage Amazon SQS messages using Amazon S3. However, you can't do this using the AWS CLI, the Amazon SQS console, the Amazon SQS HTTP API, or any of the AWS SDKs—except for the SDK for Java.

----

Which of the following technologies would you use to build and deploy Lambda functions as well as API Gateway endpoints?
   - AWS Serverless Application Model CLI
   -  CloudFormation
   
Explanation - CloudFormation and the AWS SAM CLI can be used to deploy serverless applications. Use the Transform section of the CloudFormation template to specify the serverless resources you would like to deploy. The other technologies cannot be used to deploy serverless applications. OpsWorks provides configuration management using managed instances of Puppet or Chef. Elastic Beanstalk is for deploying and scaling web applications on familiar servers such as Apache, Nginx, Passenger, and IIS. CodeBuild is an automated build system, and CodeDeploy deploys your built code to either EC2 or an on-premises server.

----

What is the CloudFormation helper script cfn-init used for?

   - Install packages and start/stop services on EC2 instance.
   
Explanation - CloudFormation helper scripts are Python scripts that can be used as part of a CloudFormation template to automate common tasks during stack creation. cfn-init helper script can be used to install packages, create files, and start/stop services. cfn-get-metadata can be used to fetch a metadata block from AWS CloudFormation and print it to standard out.

----

Which section of the CloudFormation template should you use to define your Lambda resources?

   - Resources
   
Explanation - Use the Resources section of the CloudFormation template to define the resources you are going to deploy, e.g. EC2 instances, S3 buckets, IAM roles, Lambda functions etc.

----

Your application is comprised of web servers, load balancers, application servers and databases each web server, load balancer and database needs to be configured identically across all environments. How can you achieve this with CloudFormation?

   - Use a CloudFormation Nested Stack
   
Explanation - Nested stacks provide the ability to configure multiple elements within your environment while reducing duplication of code. As your infrastructure grows, common patterns can emerge in which you declare the same components in multiple templates. You can separate out these common components and create dedicated templates for them. Then use the resource in your template to reference other templates, creating nested stacks.

----

AWS recommends that you use Multipart Upload for files larger than _____.

   - 100MB
   
----   
   
How would you recommend creating developer teams as a best practice to support this change in the long run?

   - Set up an application team to develop applications. Set up an infrastructure team to create and configure the infrastructure to run the applications. Set up a tools team to build and manage the CI/CD pipeline.
   
Explanation - AWS recommends organizing three developer teams for implementing a CI/CD environment: an application team, an infrastructure team, and a tools team. This organization represents a set of best practices that have been developed and applied in fast-moving startups, large enterprise organizations, and in Amazon itself. The teams should be no larger than groups that two pizzas can feed, or about 10-12 people. This follows the communication rule that meaningful conversations hit limits as group sizes increase and lines of communication multiply. Hiring an external consulting firm will not be beneficial in the long run. Setting up a single team is not best practice. AWS CodePipeline is a continuous integration and continuous delivery service for fast and reliable application and infrastructure updates and not used for team structuring.

----

Which of the following statements are true about the concept of blue/green deployment regarding development and deployment of your application?

   - It allows you to shift traffic between two identical environments that are running different versions of your application.
   
Explanation - With blue/green deployment, you can shift traffic between two identical environments that are running different versions of your application. It allows you to easily deploy changes to your application and roll-back on changes very quickly.

----

A company is developing its first lambda function. The function needs access to their existing EC2 instances, which are all hosted in private subnets within their VPC. What must the company do to ensure their lambda can access the EC2 instances?

   - Configure lambda's execution role to have permissions for managing an ENI within the VPC.
   - Configure the lambda function to connect the private subnets used by the EC2 instances.
   - Configure lambda's security group, so it has access to the EC2 instances.
   
Explanation - To configure a lambda to connect to a VPC, one or more subnets into which it can connect must be defined. The lambda function creates an Elastic Network Interface in one of the given subnets. It, therefore, needs an execution policy that allows it permissions to do so. The specific permissions required are in the attached AWS documentation link. The Elastic Network Interface through which the lambda connects should then be associated with one or more security groups that allow network communication to the desired destinations, over the desired ports.

----

What is the name of the SAM template property that defines the point in a Lambda function's code where execution begins?

   - Handler

Explanation - The Handler property specifies the Lambda function's entry point. For example, if the Lambda function was written in Python, and Handler was set to lambda_function.lambda_handler, execution would begin with the lambda_handler function, contained within the lambda_function.py file. Runtime refers to the language in which the Lambda function is written. For example, python3.6 or nodejs6.10, etc. Source and Index are not valid SAM template properties.

----

You want to add a cross-origin resource sharing (CORS) configuration to one of your S3 buckets. Which of the following tabs should you choose to do so?

   - Permissions
  
Explanation - To add a CORS configuration to your S3 bucket, you have to click the 'Permissions' tab and choose 'CORS configuration'. The 'Properties' tab is for configuring object settings such as versioning, transfer acceleration, and logging. The 'Management' tab is for managing object replication, analytics, and storage lifecycle. If you want to simplify bucket access by creating endpoints, you choose 'Access points'.

----

What is the maximum size of an item in a DynamoDB table?

   - 400 KB
   
Explanation - The maximum item size in DynamoDB is 400 KB.

----

Which section of the AWS Serverless Application Model template would you use to describe the configuration of a Lambda function and an API Gateway endpoint, if you were deploying your application using AWS SAM?

   - Transform
   
Explanation - Use the Transform section to describe your Serverless functions when using the serverless application model. Under the Transform section, you define the resources you want to deploy.

----

How long can a message be retained in an SQS Queue?

   -  14 days
   
Explanation - Messages will be retained in queues for up to 14 days.

----

As a developer you have built a WordPress site. Traffic to the site has increased and you have improved the site's functionality to meet the demand of your viewers since launch. Changes are coming frequently, and you are considering using AWS CloudFormation to automate the process of building test stacks, creating a change set, and executing the change set. How would you streamline this process in AWS most efficiently?

   - Create a CodePipeline separated by three stages. For each stage organize actions in a pipeline. Have CodePipeline complete all actions in a stage before the stage processes new artifacts.
   
Explanation - Continuous delivery is a release practice in which code changes are automatically built, tested, and prepared for release to production. With AWS CloudFormation and CodePipeline, you can use continuous delivery to automatically build and test changes to your AWS CloudFormation templates before promoting them to production stacks. This release process lets you rapidly and reliably make changes to your AWS infrastructure. Although you can manually interact with CloudFormation to execute the various stages, this is not the most efficient method. Amazon Inspector is an automated security assessment service which evaluates the security loopholes in deployed resources specific to EC2. Config is a monitoring and governance tool that tracks changes to your AWS environment based on rules you configure.

----

Which of the following could you NOT achieve using the Amazon SQS Extended Client Library for Java?

   - Create a new S3 bucket and move a batch of SQS messages into the bucket
   
Explanation - You can use Amazon S3 and the Amazon SQS Extended Client Library for Java to manage Amazon SQS messages stored in S3. This includes specifying when messages should be stored in S3, referencing message objects stored in S3, getting them, and deleting them.

----

You are developing a Serverless application written in Node.js, which will run on Lambda. During performance testing, you notice that the application is not running as quickly as you would like and you suspect that your Lambda function does not have enough CPU capacity. Which of the following options will improve the overall performance of your function?

   - Configure more memory for your function
 
Explanation - In the AWS Lambda resource model, you choose the amount of memory you want for your function, and are allocated proportional CPU power and other resources. For example, choosing 256MB of memory allocates approximately twice as much CPU power to your Lambda function as requesting 128MB of memory and half as much CPU power as choosing 512MB of memory. Lambda allocates CPU power linearly in proportion to the amount of memory configured.

----

A developer is building an e-commerce application which will be hosted in an ECS Cluster. To minimize the number of instances in use, she must select a strategy which will place tasks based on the least available amount of CPU or memory.
Which of the following task placement strategy should the developer implement?

   - binpack
   
Explanation

A task placement strategy is an algorithm for selecting instances for task placement or tasks for termination. Task placement strategies can be specified when either running a task or creating a new service.

Amazon ECS supports the following task placement strategies:

   - binpack - Place tasks based on the least available amount of CPU or memory. This minimizes the number of instances in use.

   - random - Place tasks randomly.

   - spread - Place tasks evenly based on the specified value. Accepted values are attribute key-value pairs, instanceId, or host. 

The scenario states that the developer must select a task placement strategy which will place tasks based on the least available amount of CPU or memory. By using bin pack strategy with CPU as the field parameter, ECS is able to place tasks onto an instance with the least available amount of CPU first, before moving on to the other instances. Hence, the correct answer is to use the binpack task placement strategy.

random is incorrect because this will place the tasks randomly, rather than placing the tasks to the instances based on the least available amount of CPU or memory.

spread is incorrect because this will place tasks evenly to the instances based on a specified value.

distinctInstance is incorrect because this is not a valid task placement strategy, but a task placement constraint. This is primarily used as a constraint to place each task on a different container instance. It can be specified when either running a task or creating a new service. 

----
