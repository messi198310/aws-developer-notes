DynamoDB

-In DynamoDB, a primary key can be composite partition/sort key.

-In DynamoDB, a primary key can be a single-attribute partition key

Message sending from ECS - What policy?
   - The policy must be attached to the ECS Task's execution role to allow the application running in the container access SQS.

Best practices for instances
   - Reserved instances provide a significant discount compared to running instances On-Demand. You can take advantage of Spot Instances 
    to run and scale applications such as stateless web services, image rendering, big data analytics, 
    and massively parallel computations. Dedicated Instances are Amazon EC2 instances that run in a VPC on hardware that is dedicated to a single customer.

Increasing performance of EBS Volumes
   - Schedule snapshots of HDD based volumes for periods of low use
   - Stripe volumes together in a RAID 0 configuration.
   - Ensure that your EC2 instances are types that can be optimized for use with EBS

Services to build with from Elastic Beanstalk
   - Auto Scaling Group
   - Elastic Load Balancer
   - EC2
   - S3
   
EXPLANATION - Except for Lambda, all of the services listed can be used to create a web server farm. 
      AWS Lambda automatically runs your code without requiring you to provision or manage servers. 
      Lambda is generally used for stateless, short-running tasks and is not suitable for long-running tasks like running a web server.

Docker commands to push image
   - Run: aws ecr get-login --no-include-email --region us-east-1 Run the docker login command that was returned in the previous step. Then run: docker push 123456789012.dkr.ecr.us-east-1.amazonaws.com/my-repository
   - Run: docker tag -i my-image latest Then run: docker push 123456789012.dkr.ecr.us-east-1.amazonaws.com/my-repository

EXPLANATION - The aws ecr get-login command provides an authorization token that is valid for 12 hours. You need to run the command which was returned by the ecr get-login command to authorize you to push images to the ECR repository. For a full list of the steps, see the link below.

Which of the following AWS services could the organization use under this new policy?
   - Fargate
   - S3
   - DynamoDB

EXPLANATION - AWS consider S3, DynamoDB, and Fargate to be serverless services.

What is the AWS recommended way of managing large messages in SQS?
   - Store the messages using S3
   - Use the Amazon SQS Extended Client Library for Java to manage SQS messages
   
Explanation - You can use Amazon S3 and the Amazon SQS Extended Client Library for Java to manage Amazon SQS messages. This is especially useful for storing and consuming messages up to 2 GB in size. Unless your application requires repeatedly creating queues and leaving them inactive or storing large amounts of data in your queue, consider using Amazon S3 for storing your data. You can use the Amazon SQS Extended Client Library for Java to manage Amazon SQS messages using Amazon S3. However, you can't do this using the AWS CLI, the Amazon SQS console, the Amazon SQS HTTP API, or any of the AWS SDKs—except for the SDK for Java.

Which of the following technologies would you use to build and deploy Lambda functions as well as API Gateway endpoints?
   - AWS Serverless Application Model CLI
   -  CloudFormation
   
Explanation - CloudFormation and the AWS SAM CLI can be used to deploy serverless applications. Use the Transform section of the CloudFormation template to specify the serverless resources you would like to deploy. The other technologies cannot be used to deploy serverless applications. OpsWorks provides configuration management using managed instances of Puppet or Chef. Elastic Beanstalk is for deploying and scaling web applications on familiar servers such as Apache, Nginx, Passenger, and IIS. CodeBuild is an automated build system, and CodeDeploy deploys your built code to either EC2 or an on-premises server.
