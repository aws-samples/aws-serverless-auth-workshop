+++
title = "Create Serverless API Backend"
weight = 32
+++

You will be creating your Serverless API built with Amazon API Gateway, AWS Lambda, and Amazon DynamoDB via a CloudFormation template. Since this workshop is focused on authentication and authorization, this template will create the backend infrastructure, but not enable any security settings and the rest of the module will enable and configure such settings.

### High-Level Instructions

Create a new WildRydes Serverless Backend stack by launching a CloudFormation stack based on the ***ServerlessBackend.yaml*** file in the module 2 folder. Name the stack `WildRydesBackend`.

This WildRydes backend CloudFormation template will provision your API Gateway deployment with Lambda functions for compute, a DynamoDB database for persistence, and an S3 bucket for photo uploads which will be used in module 3. Additionally, the necessary function invocation permissions and execution role for the Lambda function will also be provisioned.

Click on the link for the region you have chosen:  
{{< tabs name="Region" >}}
{{{< tab name="N. Virginia (us-east-1)" include="us-east-1.md" />}}
{{{< tab name="Ohio (us-east-2)" include="us-east-2.md" />}}
{{{< tab name="Oregon (us-west-2)" include="us-west-2.md" />}}
{{{< tab name="Ireland (eu-west-1)" include="eu-west-1.md" />}}
{{{< tab name="Singapore (ap-southeast-1)" include="ap-southeast-1.md" />}}
{{< /tabs >}}

{{% expand "Step-by-step instructions (expand for details)" %}}

1. Launch the CloudFormation stack from the links above, choosing the link appropriate for the region you selected for this workshop. **Be sure to select the same region as you were using previously in this workshop to launch this CloudFormation stack**

1. On the next screen, Step 2, confirm the stack name is `WildRydesBackend` and click ***Next***.

1. On the Configure Stack Options page, accept all the defaults and click ***Next***.

1. Choose to ***Acknowledge that the CloudFormation template may create IAM resources with custom names***. Finally, click ***Create stack***.

1. It will take a few minutes for the Stack to create. Choose the ***Stack Info*** tab to go to the overall stack status page and wait until the stack is fully launched and shows a status of **CREATE_COMPLETE**. Click the refresh icon to see progress updates.

1. With the **WildRydesBackend** stack selected, click on the ***Outputs*** tab and copy the value shown for the **WildRydesApiInvokeUrl** to your Cloud9 scratchpad editor tab.