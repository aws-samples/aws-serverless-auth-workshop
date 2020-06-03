+++
title = "Running the website locally"
chapter = false
weight = 22
+++

1. From your Cloud9 workspace, select the terminal window and when you are within your ***~/environment/website/*** directory, run the following command to start the local web server

    ```bash
    yarn start
    ```

    Wait for the development server to start. You can ignore any message saying ***Compiled with warnings*** as we will resolve these warnings as we add our functionality to the application. 
    
2. Now that the development server has started, click **Preview Running Application** in the top of the screen next to the Run button.

    ![Preview Running Application](../images/cloud9-local-preview.png)
    
3. The web application will load in a small window next to the terminal at the bottom of the Cloud9 IDE. Click the **re-size** button next to the word **Browser** to open this window in a new tab.

    ![resize button](../images/cloud9-resize-live-preview.png)
    
    As you make changes to the web application, this tab will automatically refresh to reflect your changes. Leave this tab open and return to the Cloud9 IDE tab to continue the workshop.

    Though the Wild Rydes website may look functional, there is currently no integration for sign-up or sign-in requests to go anywhere.
