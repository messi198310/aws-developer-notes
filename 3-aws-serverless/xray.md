X-RAY

With X-Ray, you can understand how your application and its underlying services are performing to identify and troubleshoot the root cause of performance issues and errors.

Segments - The compute resources running your application logic send data about their work as segments. A segment provides the resource’s name, details about the request, and details about the work done. e.g. host, request, response, start and end times.

Sampling - To ensure efficient tracing and provide a representative sample of the requests that your application serves, the X-Ray SDK applies a sampling algorithm to determine which requests get traced.

    Annotations 	                                          Metadata
    - Key-value pairs with string, number, or Boolean values  - Key-value pairs that can have values of any type, including objects and lists
    - Indexed for use with filter expressions 	             - Not indexed for use with filter expressions

X-Ray intergrates with the following AWS services

    -   Elastic Load Balancing
    -   AWS Lambda
    -   Amazon API Gateway
    -   EC2
    -   AWS Elastic Beanstalk

X-Ray integrates with the following languagues
- Node.js (JavaScript)
- Python
- Java (Java 8 compatible) • C# (.NET Core)
- Golang
- Ruby
- .Net
