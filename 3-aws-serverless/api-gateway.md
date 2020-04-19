API Gateway
Lambda Authorizers for API

    A Lambda authorizer (formerly known as a custom authorizer) is an API Gateway feature that uses a Lambda function to control access to your API.

    A Lambda authorizer is useful if you want to implement a custom authorization scheme that uses a bearer token authentication strategy such as OAuth or SAML, or that uses request parameters to determine the caller’s identity.

IAM authentication for API

To enable IAM authentication for your API:

    Under Settings, for Authorization, choose AWS_IAM.

    Grant API authorization to a group of IAM users i.e. add users to an IAM group and attach policies with required permissions to the group.

    Authenticate requests that are sent to API Gateway using Signature Version 4 signing process.

Caching

    To invalidate API gateway cache entry and reload it from the integration endpoint, the client must send a request that contains Cache-Control: max-age=0 header

  	 
Default TTL value for API caching 	300 seconds
Maximum TTL value for API caching 	3600 seconds
Supported Cache size 	0.5GB up to 237GB
