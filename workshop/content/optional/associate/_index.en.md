+++
title = "Associate an API Gateway"
weight = 42
+++

For us to be able to use request signing and IAM-based fine-grained access control, we'll first need to associate an IAM policy that provides permissions to invoke API operations for your API Gateway deployment. For further details, you can review [controlling access to an API with IAM permissions](https://docs.aws.amazon.com/apigateway/latest/developerguide/permissions.html) documentation.

### High-Level Instructions

In the IAM console, assocate the **WildRydesAPI-StandardUserPolicy** with your Cognito Identity Pool's authenticated user role to provide all authenticated users access to invoke operations the **/ride** path.

{{% expand "Step-by-step instructions (expand for details)" %}}

1. Go the AWS Management Console, click **Services** then select **IAM** under Security, Identity, and Compliance.

1. Choose **Policies**.

1. Search for ***WildRydes*** to see the ***WildRydesAPI-StandardUserPolicy*** which was created by the Serverless Backed CloudFormation template.

    ![WildRydes API IAM Policy Search](../images/iam-policies-wildrydesapi-search.png)

1. Click the **WildRydesAPI-StandardUserPolicy** policy name.

1. Review the policy which was created by CloudFormation to authorize requests to your API Gateway deployment.

    ![WildRydesAPI Policy Details](../images/iam-wildrydesapi-policy-details.png)

    > This policy allows access to invoke any method on the /ride path for any API stage of your API gateway backend. For more details about authoring IAM policies for API Gateway, visit the controlling access to an API with IAM permissions documentation.

1. Choose **Roles**.

1. Search for **WildRydes** to find the two roles which were created by Cognito Identity Pools when you created the Identity Pool in module one. Should you not be able to find the roles here, you can alternatively go to the **Cognito Federated Identities** console, find the correct identity pool, then click **Edit Identity Pool** in the top-right corner to see the roles listed. Each identity pool has both an Unauthenticated user role and an Authenticated user role.

1. Once you have found the names of the roles, go back to the IAM console and select the Auth role for your authenticated users.

    > If the full name of the role is hidden from view due to column width, you can hover over the partially visible name of the role to see the full name of the role as a tool tip.

    ![IAM WildRydes Auth Role Selction](../images/iam-wildrydes-role-selection.png)

1. Choose **Attach policies**.

1. Search for `WildRydes` and check the box next to the policy named ***WildRydesAPI-StandardUserPolicy***.

    ![Attach API Gateway IAM Policy](../images/iam-cognito-authrole-attach-apigateway-policy.png)

1. Choose **Attach policy**.

1. You should now see the ***WildRydesAPI-StandardUserPolicy*** policy associated with your Cognito IAM auth role.

    ![Permissions after adding IAM policy](../images/iam-cognito-authrole-permissions-after-policy-update.png)

