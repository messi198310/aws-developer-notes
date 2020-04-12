Web Identity Federation and Cognito - Order 
    A user authenticates with Facebook first. They are then given an ID token by Facebook. An API call, AssumeRoleWithWebIdentity, 
    is then used in conjunction with the ID token. A user is then granted temporary security credentials.

Lambda function written in Python to use client-side encryption
    Client-side encryption means you need to encrypt the files where they are currently stored 
    before uploading them to S3. You can do this in Lambda by using the AWS Encryption SDK.

 How can you ensure the data is encrypted end-to-end in transit between your ELB and EC2 instances?
 
   - Configure a secure listener on your load balancer
   - Terminate HTTPS connections on your EC2 instances
   -  Configure the instances in your environment to listen on the secure port
   
    
Explanation - Terminating secure connections at the load balancer and using HTTP on the backend might be sufficient for your application. However, if you are developing an application that needs to comply with strict external regulations, you might be required to secure all network connections. First, add a secure listener to your load balancer, then configure the instances in your environment to listen on the secure port and terminate HTTPS connections.

Which of the following will ensure that only encrypted data is stored in S3?

   - Use a bucket policy that only allows PUT operations which include the x-amz-server-side-encryption parameter in the request header
    
Explanation - There are a few different ways to enforce encryption, however from the provided options, the use of a bucket policy to reject requests that do not include encryption in their header is the best answer

What KMS operation should be called for each document if they must be encrypted using a unique key?

   - generate-data-key
    
Explanation - generate-data-key returns a plaintext data key, ready to be used to encrypt a document, and a ciphertext version of the key, encrypted using the Customer Master Key. The command should be called for each document, so a different key is used for each. Once the document is encrypted, the plaintext key is securely discarded, and the encrypted data key is stored along with the encrypted document. generate-data-key-without-plaintext is incorrect because it is the plaintext key that is used to encrypt the document within the application. generate-random is incorrect as while the response could be used as a data key; a second step would also be needed to acquire the ciphertext version of the key. It is, therefore, not the best solution. encrypt is incorrect because it can only encrypt up to 4 kilobytes of data, and because the encryption process itself would take place within KMS, directly using the Customer Master Key, not within the application. To that end, using 'encrypt' directly does not fall under AWS's definition of envelope encryption.

A company security team wants to implement a solution for securely storing RDS database credentials. The solution should provide automatic rotation of database credentials. What AWS service can the team use to meet these requirements?

   -  AWS Secrets Manager
    
Explanation - AWS Secrets Manager is an AWS service that can be used to securely store, retrieve, and automatically rotate database credentials. AWS Secrets Manager has built-in integration for RDS databases. Applications use Secrets Manager API's to retrieve database credentials, enabling secure storage of sensitive information outside of the application code. Systems Manager Parameter Store provides secure storage of sensitive information. However, it does not provide automatic credentials rotation capability specified as a requirement in the question scenario. Key Management Service (KMS) is used for management of cryptographic encryption keys, not for storage of sensitive information. Resource Access Manager is not applicable here as it is used for managing access to AWS resources between multiple accounts.

Your EC2 instance needs to access a number of files which have been encrypted using KMS. Which of the following must be configured in order for the EC2 instance to successfully read the files?

   - The EC2 instance must have an instance role which has permission run the decrypt operation
   - The Key Policy must allow the instance role to use the CMK

Explanation - Manage access to KMS keys using a key policy. In the key policy, you must specify the principal (the identity) that the permissions apply to. You can specify AWS accounts (root), IAM users, IAM roles, and some AWS services as principals in a key policy. You can use IAM policies in combination with key policies to control access to your customer master keys (CMKs) in AWS KMS.

You are developing a online-banking website which will be accessed by a global customer base. You are planning to use CloudFront to ensure users experience good performance regardless of their location. The Security Architect working on the project asks you to ensure that all requests to CloudFront are encrypted using HTTPS. How can you configure this?

   - Set the Viewer Protocol Policy to redirect HTTP to HTTPS
   
Explanation - Viewer Protocol Policy defines the protocols which can be used to access CloudFront content

You are developing a mobile web application using Lambda and API Gateway which stores persistent data in a DynamoDB table. You want to configure the application to allow new users to sign-up to your website using their Google mail credentials. Which is the best approach?

   - Configure a Cognito User Pool to handle new user sign-up

Explanation - Cognito is the recommended approach for user sign-up and sign-in for mobile applications which allow access to users with Facebook, Google or Amazon.com credentials. User pools are user directories that provide sign-up and sign-in options for your app users. Identity pools enable you to grant your users access to other AWS services.
