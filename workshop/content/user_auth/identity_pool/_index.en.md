+++
title = "Creating a Cognito Identity Pool"
weight = 24
+++

Cognito Identity Pools are used to provide AWS credentials via IAM roles to end-user applications. Since we'll be integrating our Cognito deployment and users with other AWS services, we'll go ahead and create this identity pool now.

### High-Level Instructions

You will need to create a Cognito Identity Pool linked to the Cognito User Pool and app client ID you just created. Your application will not require un-authenticated users to access any AWS resources, so you do not need to enable access to unauthenticated identities.

{{%expand "Step-by-step instructions (expand for details)" %}}

1. In the Cognito console, choose **Federated Identities** in the header bar to switch to the console for Cognito Federated Identities.

2. Choose Create new **Identity pool**.

3. Input `wildrydes_identity_pool` as the Identity pool name. 

4. Expand **Authentication providers**. 

5. Within the Cognito tab, input the User Pool ID and App client Id you copied previously to the scratchpad tab. 

    ![Create Identity Pool](../images/cognito-identitypool-setup-step1.png)
    
6. Choose **Create Pool**.

7. Choose **Allow** to allow Cognito Identity Pools to setup IAM roles for your application's users. Permissions and settings of these roles can be customized later.

8. Copy/paste the ***Identity Pool ID***, highlighted in red within the code sample in the Get AWS Credentials section, into your Cloud9 scatchpad editor tab.

    > Do not copy the quatation marks, but include the region code and ":" character.
                                                                                                                                                                                                                                                                                                                                    
    ![Get AWS Credentials](../images/cognito-identitypool-copyId.png)
    
9. Your scratchpad should now have values for the following Cognito resources:

    ![Cognito scratchpad](../images/cognito-setup-scratchpad.png)
    
{{% /expand %}}