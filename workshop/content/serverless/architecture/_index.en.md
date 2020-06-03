+++
title = "Solution Architecture"
weight = 31
+++

Building on Module 1, this module will add a Serverless backend built using Amazon API Gateway and AWS Lambda. For persistence, you will use Amazon DynamoDB as a NoSQL data store. All of the above services are serverless so you can seamlessly scale your application as your demands grow. After creating the API, we will integrate our client application to call it via the AWS Amplify library.

   ![Solution Architecture](../images/wildrydes-module2-architecture.png)
    
### Implementation Overview

Each of the following sections provides an implementation overview and detailed, step-by-step instructions. The overview should provide enough context for you to complete the implementation if you're already familiar with the AWS Management Console or you want to explore the services yourself without following a walkthrough.

If you're using the latest version of the Chrome, Firefox, or Safari web browsers the step-by-step instructions won't be visible until you expand the section.