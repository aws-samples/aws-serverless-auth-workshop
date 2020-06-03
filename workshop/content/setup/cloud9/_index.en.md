+++
title = "Create a Cloud9 Workspace"
weight = 13
+++

{{% notice tip %}}
Ad blockers, javascript disablers, and tracking blockers should be disabled for
the cloud9 domain, or connecting to the workspace might be impacted.
Cloud9 requires third-party-cookies. You can whitelist the [specific domains]( https://docs.aws.amazon.com/cloud9/latest/user-guide/troubleshooting.html#troubleshooting-env-loading).
{{% /notice %}}

### AWS Cloud9 IDE

[AWS Cloud9](https://aws.amazon.com/cloud9/) is a cloud-based integrated development environment (IDE) that lets you  write, run, and debug code from any machine with just a browser. It includes a code editor, debugger and terminal. Cloud9 comes pre-packaged with essential tools for popular programming languages and the AWS Command Line Interface (CLI) pre-installed so you don't need to install files or configure your laptop for this workshop.

### Launch Cloud9 IDE

In this section you will launch a CloudFormation stack that will create a new [AWS VPC](https://aws.amazon.com/vpc) environment and a [Cloud9 IDE](https://aws.amazon.com/cloud9) instance that you will use in the rest of the workshop.

Click on the link for the region you have chosen:  
{{< tabs name="Region" >}}
{{{< tab name="N. Virginia (us-east-1)" include="us-east-1.md" />}}
{{{< tab name="Ohio (us-east-2)" include="us-east-2.md" />}}
{{{< tab name="Oregon (us-west-2)" include="us-west-2.md" />}}
{{{< tab name="Ireland (eu-west-1)" include="eu-west-1.md" />}}
{{{< tab name="Singapore (ap-southeast-1)" include="ap-southeast-1.md" />}}
{{< /tabs >}}

{{%expand "Step-by-step instructions (expand to see)" %}}

1. Launch the CloudFormation stack from the links above, choosing the link appropriate for the region you selected for this workshop.

2. On the next screen, Step 2, confirm the stack name is `WildRydes-Cloud9` and click **Next**.

3. On the Configure Stack Options page, accept all the defaults and click **Next**.

4. On the Review page, review the summary details then click **Create stack**.

5. It will take a few minutes for the stack to create. Choose the **Stack Info** tab to go to the overall stack status page and wait until the stack is fully launched and shows a status of *CREATE_COMPLETE*. Click the refresh icon periodically to see progress update.

6. With the *WildRydes-Cloud9* stack selected, click on the **Outputs** tab and copy the value shown for the *Cloud9IDE* to the clipboard. Browse to that URL in a new browser tab to load your IDE environment.

    > Note: When you launch the stack, CloudFormation deploys a nested CloudFormation stack to launch the Cloud9 resources. You can safely ignore that template which is prefixed with "aws-cloud9-WildRydes-".
   
    ![cloudformation outputs](../images/cloud9_cfn_outputs.png)

{{% /expand%}}

Once you have launched and navigated to your Cloud9 workspace URL shown in your CloudFormation stack outputs, you should have an IDE environment as shown below: 

![cloud9 environment](../images/cloud9_initial_screen.png)
