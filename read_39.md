# Read: 39 - Kinesis

## ANALYTICS

![Analytics](https://th.bing.com/th/id/R.2464e8b08aad528a0e49b567eab05d03?rik=H%2fvdkq9m%2boMSIw&riu=http%3a%2f%2fdocs.aws.amazon.com%2fmobileanalytics%2flatest%2fug%2fimages%2fanalytics-overview.png&ehk=nRKtxZsp1SE7yb3pWbNsUiVx1Ey7xyiYiOzV11qoPOg%3d&risl=&pid=ImgRaw&r=0)

The Analytics category enables you to collect analytics data for your App. The Analytics category comes with built-in support for Amazon Pinpoint and Amazon Kinesis

This Reading provide you with steps and info to setup and configure your application with Amplify Analytics and record an analytics event.

## Set up Analytics backend

1. `amplify add analytics`

and choose like this:

```
? Select an Analytics provider (Use arrow keys)
    `Amazon Pinpoint`
? Provide your pinpoint resource name:
    `yourPinpointResourceName`
? Apps need authorization to send analytics events. Do you want to allow guests and unauthenticated users to send analytics events? (we recommend you allow this when getting started)
    `Yes`
```

2. To deploy your backend, run:

`amplify push`

3. To **Add analytics library:**

```
dependencies {
    // Add these lines in `dependencies`
    implementation 'com.amplifyframework:aws-analytics-pinpoint:1.29.0'
    implementation 'com.amplifyframework:aws-auth-cognito:1.29.0'
}
```

To **initialize the Amplify Auth and Analytics:**

```
Amplify.addPlugin(new AWSCognitoAuthPlugin());
Amplify.addPlugin(new AWSPinpointAnalyticsPlugin(this));
```

The class will look like this:

```
public class MyAmplifyApp extends Application {
    @Override
    public void onCreate() {
        super.onCreate();

        try {
            // Add these lines to add the AWSCognitoAuthPlugin and AWSPinpointAnalyticsPlugin plugins
            Amplify.addPlugin(new AWSCognitoAuthPlugin());
            Amplify.addPlugin(new AWSPinpointAnalyticsPlugin(this));
            Amplify.configure(getApplicationContext());

            Log.i("MyAmplifyApp", "Initialized Amplify");
        } catch (AmplifyException error) {
            Log.e("MyAmplifyApp", "Could not initialize Amplify", error);
        }
    }
}
```

To **record an event:**
Create an AnalyticsEvent and call Amplify.Analytics.recordEvent() to send it:

```
AnalyticsEvent event = AnalyticsEvent.builder()
    .name("PasswordReset")
    .addProperty("Channel", "SMS")
    .addProperty("Successful", true)
    .addProperty("ProcessDuration", 792)
    .addProperty("UserAge", 120.3)
    .build();

Amplify.Analytics.recordEvent(event);
```

To view analytics console : `amplify console analytics`

## What is Amazon Kinesis Data Streams?

Amazon Kinesis Data Streams is a fully managed service for real-time processing of streaming data at massive scale. Amazon Kinesis can collect and process hundreds of terabytes of data per hour from hundreds of thousands of sources, so you can write applications that process information in real-time. With Amazon Kinesis applications, you can build real-time dashboards, capture exceptions and generate alerts, drive recommendations, and make other real-time business or operational decisions. You can also easily send data to other services such as Amazon Simple Storage Service, Amazon DynamoDB, and Amazon Redshift.

The Kinesis Data Streams KinesisRecorder client lets you store your Kinesis requests on disk and then send them all at once using the PutRecords API call of Kinesis. This is useful because many mobile applications that use Kinesis Data Streams will create multiple requests per second. Sending an individual request under PutRecord action could adversely impact battery life. Moreover, the requests could be lost if the device goes offline. Thus, using the high-level Kinesis Data Streams client for batching can preserve both battery life and data.

To show documentation through this link :

![Kinesis](https://docs.amplify.aws/sdk/analytics/kinesis/q/platform/android/)

We gonna use **amazon pinpoint**

## Amazon PinPoint

![pinpoint](https://d1.awsstatic.com/product-marketing/Pinpoint/Product-page-diagram_Amazon-Pinpoint-with-Journeys-%402x.59f755aedb4ea26ddbdeade13529046129c3d7a1.png)

Amazon Pinpoint is a flexible and scalable outbound and inbound marketing communications service. You can connect with customers over channels like email, SMS, push, voice or in-app messaging. Amazon Pinpoint is easy to set up, easy to use, and is flexible for all marketing communication scenarios. Segment your campaign audience for the right customer and personalize your messages with the right content. Delivery and campaign metrics in Amazon Pinpoint measure the success of your communications. Amazon Pinpoint can grow with you and scales globally to billions of messages per day across channels.

To show more details visit:

- [Analytics](https://docs.amplify.aws/lib/analytics/getting-started/q/platform/android/)
- [pinpoint](https://aws.amazon.com/pinpoint/?nc=sn&loc=0)
