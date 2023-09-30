# Lambda
AWS Lambda Interview Questions
==============================

1. What is AWS Lambda?

Answer: AWS Lambda is a serverless computing service provided by Amazon Web Services. It allows you to run code without provisioning or managing servers. You can execute functions in response to events, such as changes in data in an S3 bucket or HTTP requests to an API Gateway.

2. What are the benefits of AWS Lambda?

Answer: The benefits of AWS Lambda include:

- Serverless architecture, which eliminates the need for server management.
- Automatic scaling.
- Cost-effectiveness, as you only pay for the compute time used.
- Event-driven execution.
- Easy integration with other AWS services.

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

22. How many layers can i use in lamdba?

Answer: AWS Lambda allows you to use up to five layers in a Lambda function. This includes one layer of your function code and up to four additional layers that can contain libraries, custom runtimes, or other function dependencies.

Function Code Layer: This is the primary layer that contains your Lambda function's code. It's automatically created when you deploy your Lambda function and cannot be removed or modified separately from your function code.

Additional Layers: You can attach up to four additional layers to your Lambda function. These layers can contain shared libraries, dependencies, or custom runtimes that you want to reuse across multiple functions.

23. What if i have more than 5 layers?

Answer: 

24. What is the max memory a lambda function can have?

25. How would u know if lamda is unprovisioned or over provisioned memory ?

Answer: Determining whether an AWS Lambda function is under-provisioned or over-provisioned in terms of memory allocation involves monitoring and analyzing the function's performance, duration, and resource utilization. Here are some key indicators to help you assess the memory allocation:

Under-Provisioned:

High Execution Time: If your Lambda function's execution time is consistently near or at its maximum allowed duration (e.g., 15 minutes for AWS Lambda), it may indicate that it's under-provisioned. This is especially true if your function frequently times out before completing its tasks.

Low CPU Utilization: AWS Lambda provides more CPU power as you allocate more memory to your function. If your function's CPU utilization is consistently low (indicating it's not fully utilizing the allocated memory), you might be under-provisioned.

Bottlenecks: If your function relies on external resources, such as databases or APIs, and you notice delays in processing due to waiting for these resources, it could be a sign of under-provisioning. Adding more memory may reduce these bottlenecks.

Over-Provisioned:

Low Memory Utilization: If your Lambda function consistently uses significantly less memory than what is allocated, it might be over-provisioned. AWS Lambda bills you based on allocated memory, so over-provisioning can result in higher costs.

Short Execution Times: If your Lambda function's execution times are very short, and it doesn't require the allocated memory for its tasks, it may indicate over-provisioning. Reducing memory allocation can be cost-effective in such cases.

Resource Wastage: If you are allocating a large amount of memory to a function that doesn't fully utilize it, you're essentially paying for resources that you don't need.

26. What is lambda destination?

Answer: AWS Lambda Destinations allow you to asynchronously send the results of a Lambda function's execution to various AWS services like S3, SQS, SNS, and EventBridge. This decouples your function from downstream processing, enabling efficient, error-handled, and event-driven workflows. You can configure destinations when defining the Lambda function and ensure reliable event processing with features like retries and throttling.

27. What is diff reserved concurrency and provional concurrency?

Answer: 
Reserved Concurrency:

Reserved Concurrency in AWS Lambda allows you to set a specific number of concurrent executions that are dedicated exclusively to a particular Lambda function. This ensures that the function always has those resources available to it, preventing other functions from using those resources even if they are idle. Reserved Concurrency is useful for ensuring consistent performance for critical functions and is particularly handy when you have varying workloads.

Provisioned Concurrency:

Provisioned Concurrency is a feature in AWS Lambda that allows you to pre-warm a specified number of execution environments (containers) for a function. These pre-warmed environments can significantly reduce cold start latencies by ensuring that there are ready-to-use resources when your function is invoked. Provisioned Concurrency is ideal for applications with sudden spikes in traffic or latency-sensitive workloads.

28. Functional URL and API gateway in lambda functoins?

Answer: 
It seems like you're asking about integrating AWS Lambda functions with functional URLs and API Gateway. In this context, a "functional URL" typically refers to an endpoint or URL that represents a specific function or operation exposed by an API. Amazon API Gateway is a service provided by AWS that enables you to create, publish, and manage APIs, including those that invoke AWS Lambda functions. Here's how these components work together:

**1. AWS Lambda Functions:**
   - AWS Lambda functions are units of code that can be executed in response to various events or triggers, such as HTTP requests, database changes, or scheduled events.
   - You write the code for your Lambda function, and it can perform specific tasks, calculations, or actions based on the input it receives.

**2. Amazon API Gateway:**
   - Amazon API Gateway acts as a front-end for your APIs. It allows you to define and expose RESTful or WebSocket APIs.
   - You can create API resources, methods, and endpoints that map to AWS Lambda functions. When an HTTP request is made to an API Gateway endpoint, it triggers the associated Lambda function.
   - API Gateway also provides features for authentication, authorization, request/response transformations, rate limiting, and more.
   - It acts as a central point for managing your API's endpoints, making it easier to maintain and secure your APIs.

**3. Functional URLs:**
   - Functional URLs, in this context, are the URLs or endpoints that are exposed by Amazon API Gateway and map to specific Lambda functions.
   - These URLs are used to invoke the corresponding Lambda functions by making HTTP requests (e.g., GET, POST, PUT, DELETE) to them.
   - Each functional URL can represent a specific operation or functionality of your API, such as creating a resource, retrieving data, or updating records.

**Example:**
   - Let's say you have an e-commerce application, and you want to expose an API for retrieving product information. You can create an API in API Gateway, define a resource like `/products`, and create a GET method for retrieving product details. You then associate this method with a Lambda function that fetches product data from a database.
   - The functional URL for retrieving product information could be something like `https://api.example.com/products`.

When a client makes an HTTP GET request to `https://api.example.com/products`, API Gateway invokes the associated Lambda function to retrieve and return the product data.

In summary, AWS Lambda functions can be triggered by HTTP requests through Amazon API Gateway, which provides functional URLs (endpoints) that map to specific Lambda functions, allowing you to build RESTful APIs and expose various functionalities of your application over the internet.
