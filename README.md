# Lambda
AWS Lambda Interview Questions
==============================

1. What is AWS Lambda?

Answer: AWS Lambda is a serverless computing service provided by Amazon Web Services. It allows you to run code without provisioning or managing servers. You can execute functions in response to events, such as changes in data in an S3 bucket or HTTP requests to an API Gateway.

2. What are the benefits of AWS Lambda?

Answer: The benefits of AWS Lambda include:

Serverless architecture, which eliminates the need for server management.
Automatic scaling.
Cost-effectiveness, as you only pay for the compute time used.
Event-driven execution.
Easy integration with other AWS services.

3. How do you trigger a Lambda function?

Answer: Lambda functions can be triggered by various AWS services, including:

API Gateway HTTP requests.
S3 bucket events (e.g., object creation or deletion).
AWS IoT events.
AWS CloudWatch Events.
Amazon SNS messages.
Custom events from your code.

4. What is the maximum execution time for a Lambda function?

Answer: The maximum execution time for a Lambda function is 900 seconds (15 minutes). Functions exceeding this limit will be terminated.

5. What is an AWS Lambda Layer?

Answer: A Lambda Layer is a distribution mechanism for libraries, custom runtimes, and other function dependencies. It allows you to manage common code and resources independently from your Lambda functions, reducing the deployment package size.

6. How do you handle errors in Lambda functions?

Answer: Errors in Lambda functions can be handled by logging the error details to CloudWatch Logs, notifying through SNS, or configuring dead-letter queues (DLQs) for asynchronous invocations. Additionally, you can implement error handling within your code.

7. What are the different execution environments for Lambda functions?

Answer: AWS Lambda supports multiple runtimes, including Node.js, Python, Java, Ruby, .NET Core, Go, and custom runtimes. You can choose the runtime that best suits your application.

8. What is AWS Lambda's concurrency model?

Answer: AWS Lambda manages concurrency by automatically scaling the number of function instances in response to incoming requests. The number of concurrent executions for a function can be controlled using concurrency limits.

9. What is the difference between synchronous and asynchronous invocation of Lambda functions?

Answer: Synchronous invocation means the function execution is immediate, and the result is returned to the caller. Asynchronous invocation queues the request for later execution and immediately returns a response. Asynchronous invocations are often used for decoupling components.

10. What is the cold start problem in Lambda functions, and how can you mitigate it?

Answer: The cold start problem refers to the initial delay when a Lambda function is invoked for the first time or after it has been idle. To mitigate it, you can use provisioned concurrency, which pre-warms function instances to reduce cold starts.

11. How can you pass environment variables to Lambda functions?

Answer: You can define environment variables for Lambda functions using the AWS Management Console, AWS CLI, or CloudFormation templates. These variables can be accessed in your function code.

What is the maximum package size for a Lambda deployment package?

Answer: The maximum deployment package size for a Lambda function, when uploaded directly or from an S3 bucket, is 50 MB for AWS Lambda@Edge and 250 MB for standard AWS Lambda functions


12. What is AWS Lambda Provisioned Concurrency, and when is it useful?

Answer: Provisioned Concurrency is a feature that allows you to pre-warm a specific number of function instances to handle anticipated traffic. It's useful when you want to reduce the impact of cold starts or ensure consistent performance for mission-critical functions.

13. Explain the difference between AWS Lambda and AWS Fargate.

Answer: AWS Lambda is a serverless compute service for running code in response to events, while AWS Fargate is a container service that allows you to run containers without managing the underlying infrastructure. Lambda is typically used for event-driven, short-lived functions, while Fargate is suitable for longer-running, containerized applications.

14. What are the IAM roles associated with AWS Lambda functions, and how are they used?

Answer: Lambda functions are associated with IAM (Identity and Access Management) roles. Execution roles define the permissions that the function has, while resource-based policies (e.g., S3 bucket policies) define what resources can trigger the function. IAM roles are used to grant permissions for accessing AWS services and resources.

15. How can you handle retries for failed asynchronous invocations of Lambda functions?

Answer: To handle retries, you can configure an Amazon SQS (Simple Queue Service) queue as an event source for your Lambda function. Lambda will automatically retry failed events as long as they remain in the queue. You can also configure a Dead Letter Queue (DLQ) for failed asynchronous invocations.

16. Explain the difference between AWS Step Functions and AWS Lambda.

Answer: AWS Step Functions is a serverless orchestration service for coordinating multiple AWS services and Lambda functions into serverless workflows. Lambda is a compute service for running code. While Lambda is used for executing individual functions, Step Functions are used to create workflows by coordinating the execution of Lambda functions and other services.

17. What is the difference between an AWS Lambda function and an AWS Lambda Layer?

Answer: An AWS Lambda function is a piece of code that you write and deploy to AWS Lambda. It can contain your business logic. In contrast, a Lambda Layer is a distribution mechanism for libraries, custom runtimes, or other function dependencies. Layers are useful for sharing code between multiple functions.

18. How can you monitor the performance and logs of AWS Lambda functions?

Answer: You can monitor Lambda functions using Amazon CloudWatch. Lambda automatically sends metrics to CloudWatch, and you can create alarms based on these metrics. Additionally, you can view detailed logs in CloudWatch Logs to troubleshoot issues.

19. What is the maximum timeout for a Lambda function?

Answer: The maximum timeout for a Lambda function is 15 minutes (900 seconds). Functions exceeding this limit will be terminated.

20. How can you control the concurrency of AWS Lambda functions?

Answer: You can control the concurrency of Lambda functions using the "reserved concurrency" setting. It allows you to set a maximum number of concurrent executions for a function. Additionally, you can use AWS Application Auto Scaling to automatically adjust concurrency based on metrics.

21. What is the AWS Lambda Execution Environment?

Answer: The AWS Lambda Execution Environment is the runtime environment where your Lambda function code runs. It includes the operating system, language runtime, libraries, and resources provided by AWS. AWS manages the environment, and you only need to focus on your code.
