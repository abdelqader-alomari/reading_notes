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


## @connection

The @connection directive enables you to specify relationships between @model types. Currently, this supports one-to-one, one-to-many, and many-to-one relationships. You may implement many-to-many relationships using two one-to-many connections and a joining @model type. See the usage section for details.

### Definition

`directive @connection(keyName: String, fields: [String!]) on FIELD_DEFINITION`

### Usage

Relationships between types are specified by annotating fields on an `@model` object type with the `@connection` directive.

The `fields` argument can be provided and indicates which fields can be queried by to get connected objects. The `keyName` argument can optionally be used to specify the name of secondary index (an index that was set up using `@key`) that should be queried from the other type in the relationship.

When specifying a `keyName`, the `fields` argument should be provided to indicate which field(s) will be used to get connected objects. If keyName is not provided, then `@connection` queries the target table's primary index.

### Has one
In the simplest case, you can define a one-to-one connection where a project has one team

### Has many


```
type Post @model {
  id: ID!
  title: String!
  comments: [Comment] @connection(keyName: "byPost", fields: ["id"])
}

type Comment @model
  @key(name: "byPost", fields: ["postID", "content"]) {
  id: ID!
  postID: ID!
  content: String!
}
```
one-to-many connection needs an @key that allows comments to be queried by the postID and the connection uses this key to get all comments whose postID is the id of the post was called on.

### Belongs to

You can make a connection bi-directional by adding a many-to-one connection to types that already have a one-to-many connection. In this case you add a connection from Comment to Post since each comment belongs to a post

### Many-to-many connections

You can implement many to many using two 1-M @connections, an @key, and a joining @model.


### Review Intro to Serverless and AWS Amplify Kool-Aid from my previous read link

[Serverless and Amplify](https://abdelqader-alomari.github.io/reading_notes/read_32)

## Resources

- [GraphQL @connection section](https://aws-amplify.github.io/docs/cli-toolchain/graphql#connection)
- [Review Serverless](https://hackernoon.com/what-is-serverless-architecture-what-are-its-pros-and-cons-cc4b804022e9)
- [review: AWS Amplify Kool-Aid](https://aws.amazon.com/amplify/)
