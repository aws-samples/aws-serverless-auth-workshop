+++
title = "Remove WildRydes Backend"
weight = 64
+++

Next, you will need to remove the ***CloudFormation*** stack for the API. This stack should be named **WildRydesBackend**. Once again, from the your terminal window, run:

   ```bash
   aws cloudformation delete-stack --stack-name WildRydesBackend
   ```

   > If you changed the name of your stack from the default, you will need to update the stack name to what you changed it to. If you clicked the quick link in the instructions, no adjustment to the above command is needed. You can run `aws cloudformation describe-stacks` to find the your stack name.