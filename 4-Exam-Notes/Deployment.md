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
   
   -- Except for Lambda, all of the services listed can be used to create a web server farm. 
      AWS Lambda automatically runs your code without requiring you to provision or manage servers. 
      Lambda is generally used for stateless, short-running tasks and is not suitable for long-running tasks like running a web server.

Docker commands to push image
    Run: aws ecr get-login --no-include-email --region us-east-1 Run the docker login command that was returned in the previous step. Then run: docker push 123456789012.dkr.ecr.us-east-1.amazonaws.com/my-repository
    Run: docker tag -i my-image latest Then run: docker push 123456789012.dkr.ecr.us-east-1.amazonaws.com/my-repository

    The aws ecr get-login command provides an authorization token that is valid for 12 hours. You need to run the command which was returned by the ecr get-login command to authorize you to push images to the ECR repository. For a full list of the steps, see the link below.

