+++
title = "Serverless Identity Management, AuthN, and AuthZ Workshop"
chapter = true
weight = 1
+++
In this workshop, you will build a serverless microservices application that enables users to request unicorn rides from the Wild Rydes fleet. The application will present users with a user interface for signing up, signing in, indicating their location to request a ride, and managing their rider profile.

This application architecture demonstrates end-to-end authentication and authorization patterns through the use of [Amazon Cognito](https://aws.amazon.com/cognito/), [Amazon API Gateway](https://aws.amazon.com/api-gateway/), [AWS Lambda](https://aws.amazon.com/lambda/), and [AWS Identity and Access Management (IAM)](https://aws.amazon.com/iam/). A single page [React JS](https://reactjs.org/) web app hosts the HTML, CSS and Javascript to render the front-end which then connects to a public serverless backend API built using Amazon API Gateway and AWS Lambda. Amazon Cognito provides user identity management and authentication functions to secure the backend API. Finally, DynamoDB provides a persistence layer where data is stored and retrieved via the API's Lambda function. 

![Architecture Diagram](../images/wildrydes-complete-architecture.png)


### Issues, Comments, Feedback?

I’m open source! If you see an issue, want to contribute content, or have overall feedback please open an issue or pull request in our GitHub repository: [github.com/aws-samples/aws-serverless-auth-workshop/](https://github.com/aws-samples/aws-serverless-auth-workshop/).
 
{{% button href="https://github.com/aws-samples/aws-serverless-auth-workshop/issues" icon="fas fa-bug" %}}Report an issue{{% /button %}}
{{% button href="https://aws.amazon.com/serverless/developer-tools" icon="fas fa-graduation-cap" %}}Learn more{{% /button %}}
