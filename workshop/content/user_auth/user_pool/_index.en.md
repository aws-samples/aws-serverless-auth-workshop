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
    
3. Choose **Manage User Pools**.

4. Choose **Create a User Pool** in the top right of the console.

5. Provide a name for your user pool such as `WildRydes`.

6. Choose **Step through settings** to configure our user pool options.

    ![User Pool Configuration](../images/cognito-userpool-setup-step1.png)
    
7. Leave **Username** selected, but additionally select **Also allow sign in with verified email address** and **Also allow sign in with verified phone number**.

8. Leave all other attribute defaults as-is.

9. Choose **Next step**.

    ![User Pool attributes](../images/cognito-userpool-setup-step2.png)
    
10. Leave password policies and user sign up settings set to default setting and choose **Next Step**. 

    ![User pool password settings](../images/cognito-userpool-setup-step3.png)
    
11. Leave **MFA set to Off** for this workshop.

12. Leave the default setting selected of requiring e-mail verification. 

13. Choose **Next step**.

    ![User pool MFA settings](../images/cognito-userpool-setup-step4.png)
    
14. Leave all message and SES defaults as-is and choose **Next step**.

15. Skip adding any tags and click **Next step**.

16. Choose **No** to not remember your user's devices then click **Next step**.

    ![User pool device setting](../images/cognito-userpool-setup-step5.png)
    
17. In the next screen, click the **Add an app client** link. 

18. Input `wildrydes-web-app` as the app client name.

19. **Uncheck** ***Generate client secret***. Client secrets are used for server-side applications authentication and are not needed for JavaScript applications.

20. Choose **Create app client**.

21. Choose **Next step**.

    ![User pool app clients](../images/cognito-userpool-setup-step6.png)
    
22. Leave all Lambda trigger settings set to none. These trigger settings allow you to extend the out-of-the-box sign-up and sign-in flows with your own custom logic, but we will not be using this feature in this workshop.

23. Choose **Next step**. 

24. Review summary of all provided settings for accuracy then choose **Create Pool**. 

    ![User pool create pool](../images/cognito-userpool-setup-step7.png)
    
25. Within Cloud9, click the + symbol and choose to create **New File**. You will use this new blank editor tab as a scratchpad for various resource names and variables.

    ![Cloud9 Scratchpad](../images/cloud9-createscratchpadtab.png)
    
26. Back in the AWS Cognito console, copy your new User Pool Id into the scratchpad tab.

    ![Cognito Pool ID](../images/cognito-userpool-copy-userpool-id.png)
    
27. Choose **App clients** heading under General settings within the Cognito navigation panel.

28. Copy the ***App client ID*** over to your scratchpad. You will be using both of these values later on.

    ![Cognito App Client ID](../images/cognito-userpool-copy-appclient-id.png)

{{% /expand %}} 