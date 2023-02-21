+++
title = "Creating Cognito User Pool"
chapter = false
weight = 23
+++

Amazon Cognito User Pools lets you add user sign-up and sign-in capabilities to your web and mobile apps quickly and easily. In this step, we'll create a Cognito user pool for our Wild Rydes app.

### High-Level Instructions

Use the AWS console to create an Amazon Cognito User Pool requiring e-mail verification

{{% notice tip%}}
The console's region will default to the last region you were using previously. Change this to the same region where you launched your Cloud9 environment previously.
{{% /notice %}}

{{% expand "Step-by-Step instructions (expand for details)" %}}
1. In the AWS Management Console choose **Services** then select **Cognito** under Security, Identity, and Compliance.
    
2. Choose your desired **Region** in top-right of the console if not already selected. This should match the region where you launched your Cloud9 environment previously.
    
3. Choose **Create User Pool**.

    ![User Pool Configuration](../images/cognito-create-user-pool.png)

4. Under **Cognito user pool sign-in options**, check User name, Email, and Phone Number checkboxes, then select **Next**.

5. Leave the Password Policy defaults, then scroll down to Multi-factor authentication and select **No MFA**.  

    ![User Pool MFA Options](../images/cognito-mfa-options.png)

6.  Leave all other defaults settings, then select **Next**.
    
7. On the **Configure sign-up experience** page, leave all defaults and select **Next**.

8. On the **Configure message delivery** page, select **Send email with Cognito**.

    ![Cognito Message Delivery](../images/cognito-message-delivery.png)

9. Scroll down to the **SMS** section, then select **Create a new IAM role** and enter **wildrydes-cognito-messages** for the IAM role name. Then select **Next**.

    ![Cognito Messages IAM Role](../images/cognito-wildrydes-messages.png)
    
10. Next, enter `WildRydes` as the **User pool name**. 
    
11. Next, scroll down to the **Initial app client** section and leave Public client selected. For App client name, enter `wildrydes-web-app`.  

12. Make sure **Don't generate a client secret** is selected, then click **Next**

13. Review the summary of all provided settings for accuracy then choose **Create user pool**. 
    
14. Within Cloud9, click the + symbol and choose to create **New File**. You will use this new blank editor tab as a scratchpad for various resource names and variables.

    ![Cloud9 Scratchpad](../images/cloud9-createscratchpadtab.png)
    
15. Back in the AWS Cognito console, copy your new User Pool Id into the scratchpad tab.

    ![Cognito Pool ID](../images/cognito-userpool-copy-userpool-id.png)
    
16. Click the **App Integration** tab and scroll all the way down to the bottom.  Then copy the Client ID into the scratch tab.

    ![Cognito App Clients](../images/cognito-app-clients.png)

17. Copy the ***App client ID*** over to your scratchpad. You will be using both of these values later on.

    ![Cognito App Client ID](../images/cognito-userpool-copy-appclient-id.png)

{{% /expand %}} 