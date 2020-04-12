Web Identity Federation and Cognito - Order 
    A user authenticates with Facebook first. They are then given an ID token by Facebook. An API call, AssumeRoleWithWebIdentity, 
    is then used in conjunction with the ID token. A user is then granted temporary security credentials.

Lambda function written in Python to use client-side encryption
    Client-side encryption means you need to encrypt the files where they are currently stored 
    before uploading them to S3. You can do this in Lambda by using the AWS Encryption SDK.

 How can you ensure the data is encrypted end-to-end in transit between your ELB and EC2 instances?
   -- Configure a secure listener on your load balancer
   -- Terminate HTTPS connections on your EC2 instances
   --  Configure the instances in your environment to listen on the secure port
    
Explanation - Terminating secure connections at the load balancer and using HTTP on the backend might be sufficient for your application. However, if you are developing an application that needs to comply with strict external regulations, you might be required to secure all network connections. First, add a secure listener to your load balancer, then configure the instances in your environment to listen on the secure port and terminate HTTPS connections.

Which of the following will ensure that only encrypted data is stored in S3?
    - Use a bucket policy that only allows PUT operations which include the x-amz-server-side-encryption parameter in the request header
    
Explanation - There are a few different ways to enforce encryption, however from the provided options, the use of a bucket policy to reject requests that do not include encryption in their header is the best answer

What KMS operation should be called for each document if they must be encrypted using a unique key?
    - generate-data-key
    
Explanation - generate-data-key returns a plaintext data key, ready to be used to encrypt a document, and a ciphertext version of the key, encrypted using the Customer Master Key. The command should be called for each document, so a different key is used for each. Once the document is encrypted, the plaintext key is securely discarded, and the encrypted data key is stored along with the encrypted document. generate-data-key-without-plaintext is incorrect because it is the plaintext key that is used to encrypt the document within the application. generate-random is incorrect as while the response could be used as a data key; a second step would also be needed to acquire the ciphertext version of the key. It is, therefore, not the best solution. encrypt is incorrect because it can only encrypt up to 4 kilobytes of data, and because the encryption process itself would take place within KMS, directly using the Customer Master Key, not within the application. To that end, using 'encrypt' directly does not fall under AWS's definition of envelope encryption.

