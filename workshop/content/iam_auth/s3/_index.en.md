+++
title = "Setup S3 Bucket"
weight = 52
+++

You will need to configure AWS Amplify to securely store profile images in an S3 bucket. To save time, the Serverless Backend CloudFormation template that created the serverless backend API for this workshop also created an S3 bucket for this purpose with the cross-origin resource sharing (CORS) settings already set. You just need to associate this bucket with your application's code.

### High-Level Instructions

Browse to your CloudFormation stack created in the earlier modules and find the name of the S3 bucket under Outputs. Once you have the name, open your ***amplify-config.js*** file again and update the storage section with the bucket's name and region.

{{% expand "Step-by-step instructions (expand for details)" %}}

1. Go the AWS Management Console, click **Services** then select **CloudFormation** under Management Tools.

1. In the CloudFormation console, click on your Wild Rydes stack name, such as **WildRydesBackend**.

1. Click on the **Outputs** tab.

1. Copy your bucket name to your clipboard. It is the name shown under `Value` for the key called ***WildRydesProfilePicturesBucket***.

1. Next, return to your Cloud9 IDE and open the file **/website/src/amplify-config.js**.

1. Fill in values for both the bucket name, which you just copied, as well as the region where your CloudFormation template was launched

1. Your final structure for the storage configuration of **amplify-config.js** should look like the following.

    ```javascript
    Storage: {
        bucket: 'wildrydes-profilepicturesbucket-1rmvuic97osxd',
        region: 'us-east-1'
    }
    ```
