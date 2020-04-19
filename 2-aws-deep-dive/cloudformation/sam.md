SAM

    The AWS Serverless Application Model (SAM) is an open-source framework for building serverless applications.

    You use the AWS SAM specification to define your serverless application.

    The declaration Transform: AWS::Serverless-2016-10-31 is required for AWS SAM templates.

    Resources section is required for AWS SAM templates.

    Some of the supported SAM resource and property types - AWS::Serverless::Api, AWS::Serverless::Function, AWS::Serverless::SimpleTable.

    After you develop and test your serverless application locally, you can deploy your application by using the sam package and sam deploy commands.

    sam package and sam deploy commands described in this section are identical to their AWS CLI equivalent commands aws cloudformation package and aws cloudformation deploy, respectively.
