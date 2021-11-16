# Read: 38 - Notifications

![Notification](https://d1.awsstatic.com/diagrams/Product-page-diagram-Amazon-SNS_event-driven-SNS-compute%402X_.4b9c0a75aa40bda9cdb12f0176930a12da2872bf.png)

## Amazon Simple Notification Service

- Fully managed pub/sub messaging, SMS, email, and mobile push notifications.

- Is a fully managed messaging service for both application-to-application (A2A) and application-to-person (A2P) communication.

- The A2A pub/sub functionality provides topics for high-throughput, push-based, many-to-many messaging between distributed systems, microservice, and event-driven serverless applications.

- Using Amazon SNS topics, your publisher systems can fan out messages to a large number of subscriber systems including Amazon SQS queues, AWS Lambda functions and HTTPS endpoints, for parallel processing, and Amazon Kinesis Data Firehose.

- The A2P functionality enables you to send messages to users at scale via SMS, mobile push, and email.

## Benefits

- Modernize and decouple your applications.

- Send messages directly to millions of users.

- Reliably deliver messages.

- Automatically scale your workload.

- Ensure accuracy with message ordering and de duplication.

- Simplify your architecture with Message Filtering.

## Prerequisites

Step 1: Create a topic

Step 2: Create a subscription to the topic

Step 3: Publish a message to the topic

Step 4: Delete the subscription and topic

## how it works

you first have to create a topic, which is an access point for subscribers interested in receiving notifications about a specific subject. When a message is published to a topic, Amazon SNS pushes the message to all appropriate subscribers, which could be HTTP endpoints, Amazon SQS queues, or AWS Lambda functions.

## VPC

Amazon Virtual Private Cloud (VPC) is a virtual network that closely resembles a traditional network that you’d operate in your own data center.

Amazon VPC lets you provision a logically isolated section of the AWS Cloud where you can launch AWS resources in a virtual network that you define.

## Publish Amazon SNS Messages Privately

![messages privately](https://d1.awsstatic.com/Getting%20Started/publish-sns-message-privately-vpc-ec2-cloudformation-lambda/publish-sns-message-privately-vpc-ec2-cloudformation-lambda-1.3e2ade6aba6797824741524b668dce86dee5e79c.png)

Some common cases for private networking and messaging include:

- Isolating development and testing environments
- Sharing personally identifiable information (PII) about your customers
- Hosting a PCI-compliant e-commerce website
- Developing healthcare applications subject to HIPAA
- Implementing a cryptographic algorithm subject to FIPS 140
- Processing mortgage applications in a banking system

## Publish a message to the topic

- In the left navigation pane, choose Topics.
- On the Topics page, choose the topic that you created earlier, and then choose Publish message.
- The console opens the Publish message to topic page.
- (Optional) In the Message details section, enter a Subject, such as:
  `Hello from Amazon SNS!`
- In the Message body section, choose Identical payload for all delivery protocols, and then enter a message body, such as:
  `Publishing a message to an SNS topic.`

- Choose Publish message.
- The message is published to the topic, and the console opens the topic's Details page.
- Check your email inbox and verify that you received an email from Amazon SNS with the published message.

## References

- [SNS: Getting Started](https://aws.amazon.com/sns/getting-started/)
- [SNS with Amplify (and Firebase)](https://aws-amplify.github.io/docs/android/push-notifications)
