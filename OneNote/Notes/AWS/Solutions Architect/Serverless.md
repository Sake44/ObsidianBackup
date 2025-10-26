**With serverless compute, you can spend time on the things that differentiate your application, rather than spending time on ensuring availability, scaling, and managing servers.** Every definition of serverless mentions the following four aspects:

- There are no servers to provision or manage.
- It scales with usage.
- You never pay for idle resources.
- Availability and fault tolerance are built in.

### AWS Fargate
AWS Fargate is a purpose-built serverless compute engine for containers. AWS Fargate scales and manages the infrastructure, so developers can work on what they do best, application development.
![[Pasted image 20251026154307.png]]

### AWS Lambda

**With AWS Lambda, there are no servers to manage. You get continuous scaling with subsecond metering and consistent performance.**
 
With Lambda, you can run code without provisioning or managing servers. You can run code for virtually any type of application or backend service. This includes data processing, real-time stream processing, machine learning, WebSockets, IoT backends.
 
#### How Lambda works
The Lambda function is the foundational principle of AWS Lambda. You have the option of configuring your Lambda functions using the Lambda console, Lambda API, AWS CloudFormation, or AWS Serverless Application Model (AWS SAM). You can invoke your function directly by using the Lambda API, or you can configure an AWS service or resource to invoke your function in response to an event.

#### Billing granularity
With Lambda, you can run code without provisioning or managing servers, and you pay only for what you use. You are charged for the number of times that your code is invoked (requests) and for the time that your code runs, rounded up to the nearest 1 millisecond (ms) of duration.
 
AWS rounds up duration to the nearest ms with no minimum run time. With this pricing, it can be cost effective to run functions whose execution time is very low, such as functions with durations under 100 ms or low latency APIs.

**Resources**  
For more information, see the following resources:
 
- AWS website: [Building Applications with Serverless Architectures(opens in a new tab)](https://aws.amazon.com/lambda/serverless-architectures-learn-more/)
- AWS blog: [Best Practices for Organizing Larger Serverless Applications(opens in a new tab)](https://aws.amazon.com/blogs/compute/best-practices-for-organizing-larger-serverless-applications/)
- AWS developer guide: [Configuring AWS Lambda Functions(opens in a new tab)](https://docs.aws.amazon.com/lambda/latest/dg/lambda-functions.html)
- AWS blog: [10 Things Serverless Architects Should Know(opens in a new tab)](https://aws.amazon.com/blogs/architecture/ten-things-serverless-architects-should-know/)
- AWS workshop: [AWS Alien Attack: A Serverless Adventure(opens in a new tab)](https://alienattack.workshop.aws/)
- AWS blog: [Resize Images on the Fly with Amazon S3, AWS Lambda, and Amazon API Gateway(opens in a new tab)](https://aws.amazon.com/blogs/compute/resize-images-on-the-fly-with-amazon-s3-aws-lambda-and-amazon-api-gateway/)
- AWS blog: [New for AWS Lambda – 1ms Billing Granularity Adds Cost Savings](https://aws.amazon.com/blogs/aws/new-for-aws-lambda-1ms-billing-granularity-adds-cost-savings/)