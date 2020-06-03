+++
title = "AWS integration with IAM-based AuthZ"
chapter = true
weight = 50
pre = "<b>3. </b>"
+++

In this module, you will expand your Wild Rydes application by enabling a profile management and profile photo management capabilities. [Amazon Cognito](https://aws.amazon.com/cognito/) will be used to store your user's profile information and custom attributes whereas [Amazon S3](https://aws.amazon.com/s3/) will store your user's profile pictures, with a link to the photo only being stored in the user's profile directly.