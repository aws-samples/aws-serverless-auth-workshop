+++
title = "Configure IAM permissions"
weight = 53
+++

Though you could now attempt uploading photos via AWS Amplify, Amplify would use your Cognito Identity Pool roles that were created in module 1 which currently has no policies associated so you would not have access to the S3 bucket created. You need to next update our roles to have policies that grant access to our S3 photo bucket.

### High-Level Instructions

Browse to the IAM console and find your Cognito Identity Pool's authenticated user role. Create an in-line policy on this role which provides for [S3 bucket protected and private-level access](https://aws-amplify.github.io/docs/js/storage#file-access-levels) per-user by leveraging IAM policy variables.

{{% expand "Step-by-step instructions (expand for details)" %}}

1. Go the AWS Management Console, click **Services** then select **IAM** under Security, Identity, and Compliance.

1. Choose **Roles**.

1. Search for ***WildRydes*** to find the two roles which were created by Cognito Identity Pools when you created the Identity Pool in module one. Should you not be able to find the roles here, you can alternatively go to the **Cognito Federated Identities** console, find the correct identity pool, then click **Edit Identity Pool** in the top-right corner to see the roles listed. Each identity pool has both an Unauthenticated user role and an Authenticated user role.

1. Once you have found the names of the roles, go back to the IAM console and select the Auth role for your authenticated users.

    > If the full name of the role is hidden from view due to column width, you can hover over the partially visible name of the role to see the full name of the role as a tool tip.

    ![IAM WildRydes Auth Role Selction](../images/iam-wildrydes-role-selection.png)

1. We want to grant permissions to this role explicitly so we will use an inline policy, which would be deleted with this role if it were ever to be deleted.

1. Choose **Add inline policy** on the right-hand side to create a new inline policy associated to this IAM role.

    ![Add inline policy to WildRydes auth role](../images/iam-wildrydes-auth-role-add-inline-policy.png)

1. Choose the **JSON** tab to allow you to free-form edit the new policy.

1. Paste the following IAM policy statements for S3 access. After pasting, you will need to go **replace the bucket name** listed in all caps with your bucket name (a total of 4 times).

    > Be sure to leave the parts of the resource names before and after the replacement value alone and not accidentally modify them.

    > The following policy makes use of IAM policy variables where ***${aws:userid}*** represents the current authenticated user's unique Cognito identity ID. This policy's effective permissions will allow all authenticated users to read objects from the root of the bucket and any /protected path, but only allow users to read their own private sub-path and write to their sub-path within the protected path. These are default paths that are integrated with AWS Amplify to easily set [file access levels](https://aws-amplify.github.io/docs/js/storage#file-access-levels).

    ```
    {
        "Version": "2012-10-17",
        "Statement": [
            {
                "Effect": "Allow",
                "Action": [
                    "s3:PutObject",
                    "s3:GetObject",
                    "s3:GetObjectVersion",
                    "s3:DeleteObject",
                    "s3:DeleteObjectVersion"
                ],
                "Resource": "arn:aws:s3:::REPLACE_WITH_YOUR_BUCKET_NAME/private/${aws:userid}/*"
            },
            {
                "Effect": "Allow",
                "Action": [
                    "s3:GetObject",
                    "s3:GetObjectVersion"
                ],
                "Resource": "arn:aws:s3:::REPLACE_WITH_YOUR_BUCKET_NAME/protected/*"
            },
            {
                "Effect": "Allow",
                "Action": [
                    "s3:PutObject",
                    "s3:DeleteObject",
                    "s3:DeleteObjectVersion"
                ],
                "Resource": "arn:aws:s3:::REPLACE_WITH_YOUR_BUCKET_NAME/protected/${aws:userid}/*"
            },
            {
                "Effect": "Allow",
                "Action": [
                    "s3:PutObject",
                    "s3:GetObject",
                    "s3:GetObjectVersion",
                    "s3:DeleteObject",
                    "s3:DeleteObjectVersion"
                ],
                "Resource": "arn:aws:s3:::REPLACE_WITH_YOUR_BUCKET_NAME/public/*"
            }
        ]
    }
    ```

1. Choose **Review** policy.

1. Name the policy `WildRydes-S3Access`.

1. After reviewing for accuracy and any syntax errors, choose **Create policy**.
