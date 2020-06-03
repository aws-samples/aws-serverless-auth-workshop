+++
title = "Remove Cognito Resources"
weight = 62
+++

1. From your **Cloud9 developer environment** run the following:

    ```bash
    aws cognito-identity delete-identity-pool --identity-pool-id YOUR-IDENTITY-POOL-ID-HERE
    ```
   
    > Copy and paste your Cognito identity pool ID from your scratch pad (example: us-west-2:b4b755cd-d359-42a1-9b49-f0e73f5b2571).

    > If you closed your scratch pad with your Cognito idenity pool ID, you can run the following list call via CLI to find the proper identiy pool ID, then run the delete call above.

    ```bash
    aws cognito-identity list-identity-pools --max-results 10
    ```
   
1. Next, run the following command to delete the Cognito User Pool you created:

    ```bash
    aws cognito-idp delete-user-pool --user-pool-id YOUR-USER-POOL-ID-HERE
    ```
   
    > Copy and paste your user pool ID from your scratch pad (example: us-west-2:us-west-2_srLwFQiEC)

    > If you closed your scratch pad with your user pool ID, you can run the following list call via CLI to find the proper user pool id, then run the delete call above.

    ```bash
    aws cognito-idp list-user-pools --max-results 10
    ```
