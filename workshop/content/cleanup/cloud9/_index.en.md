+++
title = "Remove Cloud9 and VPC Stack"
weight = 65
+++

Lastly, you will need to remove the ***CloudFormation Stack*** for the **Cloud9 instance** and its VPC. This stack should be named **WildRydes-Cloud9**. Deleting this stack will **shut down and permanently delete your Cloud9 environment** and all code or projects within so be sure you want to proceed before executing this command.

   ```bash
   aws cloudformation delete-stack --stack-name WildRydes-Cloud9
   ```
    
   > If you changed the name of your stack from the default, you will need to update the stack name to what you changed it to. If you clicked the quick link in the instructions, no adjustment to the command above is needed. You can run `aws cloudformation describe-stacks` to find your stack name.