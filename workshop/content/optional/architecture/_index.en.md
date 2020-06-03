+++
title = "Solution Architecture"
weight = 41
+++

Building on Module 2, this module updates our Serverless backend built earlier using Amazon API Gateway and AWS Lambda to use IAM-based authorization. This extends our authorization capability to offer fine-grained access control authorizing differently per API operation and enhancing security via request signing. By enabling IAM-based authorization, you will use the same type of authentication, authorization, and request signing used by all AWS services and SDKs.

[Request signing](https://docs.aws.amazon.com/general/latest/gr/signing_aws_api_requests.html) is a more secure implementation of API request authentication where each API request made is signed with a signature unique to the request itself. Hence, no static API keys or bearer tokens are directly sent to the backend service and any man-in-the-middle attacks would not be able to use such API keys or bearer tokens to impersonate a valid user with the backend resources. AWS APIs and SDKs use a request signing algorithm named [Signature V4 (Sigv4)](https://docs.aws.amazon.com/general/latest/gr/signature-version-4.html) which is what you will enable your API to use in this module.

   > For production APIs, you should use either the token-based authorization OR request signing authorization via IAM demonstrated in this module, but not use both for the same API.

   ![Module 2 architecture](../images/wildrydes-module2-architecture.png)
   
---
#### Implementation Overview

Each of the following sections provides an implementation overview and detailed, step-by-step instructions. The overview should provide enough context for you to complete the implementation if you're already familiar with the AWS Management Console or you want to explore the services and documentation yourself without following a walkthrough.

If you're using the latest version of the Chrome, Firefox, or Safari web browsers the step-by-step instructions won't be visible until you expand the section.
