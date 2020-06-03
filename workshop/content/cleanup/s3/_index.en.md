+++
title = "Empty and remove S3 Bucket"
weight = 61
+++

1. First, you need to empty the ***S3 bucket*** that was created by the Serverless Backend CloudFormation template.

1. Go the AWS Management Console, click **Services** then select **CloudFormation** under Management Tools.

1. In the **CloudFormation** console, click on your ***Wild Rydes*** stack name, such as `WildRydesBackend`.

1. Click on the **Outputs** tab.

1. Copy your bucket name to your clipboard. It is the name shown under Value for the key called `WildRydesProfilePicturesBucket`.

1. Open your Cloud9 developer environment.

1. Within the Cloud9 IDE, open up a terminal. You can do this by clicking the `+` icon in the lower pane and selecting **New Terminal**.

    ![Cloud9 Terminal](../images/cloud9-new-terminal.png)

1. Paste the following command and be sure to update your S3 bucket name:

    ```bash    
    aws s3 rb s3://MY-BUCKET-NAME --force
    ```