Web Identity Federation and Cognito - Order 
    A user authenticates with Facebook first. They are then given an ID token by Facebook. An API call, AssumeRoleWithWebIdentity, 
    is then used in conjunction with the ID token. A user is then granted temporary security credentials.

Lambda function written in Python to use client-side encryption
    Client-side encryption means you need to encrypt the files where they are currently stored 
    before uploading them to S3. You can do this in Lambda by using the AWS Encryption SDK.

