# Read: 33 - GraphQL @connection

## GraphQL @connection section

![GraphQL](https://cxlabs.sap.com/wp-content/uploads/2019/05/graphql_kyma-1024x731.png)

The Amplify CLI provides GraphQL directives to enhance your schema with additional capabilities such as custom indexes, authorization rules, function triggers, and more.

- Amplify-provided directives
- @model: Defines top level object types in your API that are backed by Amazon DynamoDB
- @key: Configures custom index structures for @model types
- @auth: Defines authorization rules for your @model types and fields
- @connection: Defines 1:1, 1:M, and N:M relationships between @model types
- @function: Configures a Lambda function resolvers for a field
- @http: Configures an HTTP resolver for a field
- @predictions: Queries an orchestration of AI/ML services such as Amazon Rekognition, Amazon Translate, and/or Amazon Polly
- @searchable: Makes your data searchable by streaming it to Amazon OpenSearch
- @versioned: Defines the versioning and conflict resolution strategy for an @model type

### AWS AppSync-provided directives

The following directives are supported by the AppSync service and can be used within the Amplify GraphQL schemas. These will not be processed by Amplify CLI but passed through to the service as is and will be present in the output schema. For example, Amplify's @auth directive will add these directives under the hood to the output schema.

- @aws_api_key
- @aws_iam
- @aws_oidc
- @aws_cognito_user_pools
- @aws_auth
- @aws_subscribe

## 3rd party directives

- @algolia: Add serverless search to your Amplify API with Algolia
- @ttl: Enable DynamoDB's time-to-live feature to auto-delete old entries in your AWS Amplify API
- @firehose: Add a simple interceptor to all of your Amplify API mutations and queries
- @retain: Enable the "Retain" deletion policy for your Amplify-generated DynamoDB tables

### Review Intro to Serverless and AWS Amplify Kool-Aid from my previous read link

[Serverless and Amplify](https://abdelqader-alomari.github.io/reading_notes/read_32)

## Resources

- [GraphQL @connection section](https://aws-amplify.github.io/docs/cli-toolchain/graphql#connection)
- [Review Serverless](https://hackernoon.com/what-is-serverless-architecture-what-are-its-pros-and-cons-cc4b804022e9)
- [review: AWS Amplify Kool-Aid](https://aws.amazon.com/amplify/)