+++
title = "Update application"
weight = 54
+++

Now that your IAM policies and Amplify SDK are initialized, you will be able to upload photos and render S3 photos with minimal code using Amplify's built-in UI components. S3 image is the component used to both render image objects for a React application, as well as embeding an image picker to help with uploads.

### High-Level Instructions

Authenticate in the Wild Rydes app if you're not already logged in, then browse to the ***/profile*** path. You will see that your Cognito User Pool attributes are being read dynamically by the system. Next, you will add an [image picker](https://aws-amplify.github.io/docs/js/storage#s3image) from AWS Amplify to render a UI component for uploading and displaying photos stored in S3. These profile photos will be used to personalize the rider experience so unicorns know who to look for when picking up passengers.

{{% expand "Step-by-step instructions (expand for details)" %}}

1. After logging in to Wild Rydes (if you're not authenticated already), browse to the **/profile** path.

1. You should see that your e-mail address and phone number you registered with are displayed which are all of your currently populated attributes.

1. Open your Cloud9 IDE environment and open the file at ***/website/src/pages/Profile.js***.

1. **Uncomment** the line that says ***S3Image***. This instantiates an Amplify UI component for React apps for image rendering and uploading and only requires this single line of code.

1. Go back to the Wild Rydes app and visit the **/profile** path after logging in. You should now be able to upload photos with the new image picker.