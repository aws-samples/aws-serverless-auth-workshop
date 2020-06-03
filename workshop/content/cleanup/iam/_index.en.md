+++
title = "Detach IAM Policy"
weight = 63
+++

#### Detach CognitoIdentityPoolAuthStandardPolicy IAM Policy

1. Before you delete the backend stack, you will need to remove the IAM Policy that you manually attached to the Auth role.

    Navigate to the Identity and Access Management (IAM) Console and search for the Auth role and click into it.

    ![Find Auth Role](../images/iam-cleanup-findAuthRole.png)

1. On the Role Summary page, find the policy named **WildRydesAPI-StandardUserPolicy** in the Permissions tab. Once you locate the policy, click the **X** to remove this policy from the IAM Role. A popup window will ask you to confirm that you want to remove it - click the red **Detach** button.