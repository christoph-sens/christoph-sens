# Hi, I'm Christoph Sens 👋

Freelance IT consultant and developer from Germany. I help teams build, migrate and run software on
AWS: backend development in Java and Kotlin (Spring, Quarkus, JEE), single-page apps, CI/CD
pipelines, and step-by-step migrations without a big bang. I also coach teams, on site or
remotely via pair programming.

🌐 [christoph-sens.com](https://www.christoph-sens.com/) · Projektanfragen gern auch auf Deutsch.

## Open source: the overflow family

Kotlin libraries for sending SQS and SNS messages larger than the service limit. The payload goes to
S3 and only a pointer travels through the queue or topic. Built on
[aws-sdk-kotlin](https://github.com/awslabs/aws-sdk-kotlin) and coroutines, no Jackson dependency,
published on Maven Central with signed build provenance.

| Library | What it does | |
|---|---|---|
| [s3overflow](https://github.com/christoph-sens/s3overflow) | Payload store: offloads payloads to S3 and resolves pointers | [![Maven Central](https://img.shields.io/maven-central/v/com.christoph-sens/s3overflow)](https://central.sonatype.com/artifact/com.christoph-sens/s3overflow) |
| [sqsoverflow](https://github.com/christoph-sens/sqsoverflow) | Kotlin port of `amazon-sqs-java-extended-client-lib` | [![Maven Central](https://img.shields.io/maven-central/v/com.christoph-sens/sqsoverflow)](https://central.sonatype.com/artifact/com.christoph-sens/sqsoverflow) |
| [snsoverflow](https://github.com/christoph-sens/snsoverflow) | Kotlin port of `amazon-sns-java-extended-client-lib` | [![Maven Central](https://img.shields.io/maven-central/v/com.christoph-sens/snsoverflow)](https://central.sonatype.com/artifact/com.christoph-sens/snsoverflow) |

```kotlin
val client = SqsExtendedClient(
    SqsClient.fromEnvironment(),
    SqsExtendedClientConfig(payloadStore = S3BackedPayloadStore(s3Client, bucketName = "my-payload-bucket")),
)
client.sendMessage(SendMessageRequest { queueUrl = myQueueUrl; messageBody = largePayload })
```

Also: [ci-workflows](https://github.com/christoph-sens/ci-workflows), my shared, SHA-pinned GitHub
Actions workflows for Gradle builds, CodeQL, dependency review and container releases.
