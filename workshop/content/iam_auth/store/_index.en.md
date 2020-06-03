+++
title = "Store Profile Pics in Profile"
weight = 55
+++

With our image uploads now working, all will work as expected until you close your browser, but at that point the reference between your user profile and your profile picture will be lost. To fix this, you will leverage a Cognito User Pools user attribute called ***picture*** to persist the S3 object key so the same image can be loaded upon each login and persisted to be shown to the unicorns when you request a ride. You will need to update ***/website/src/pages/Profile.js*** and a method called ***onImageLoad*** to make this possible.

### High-Level Instructions

Implement a method to persist the images uploaded to the current user's Cognito ***picture*** attribute each time the image is changed.

{{% expand "Step-by-step instructions (expand for details)" %}}

1. Open your Cloud9 IDE environment and open the file at ***/website/src/pages/Profile.js***.

1. The S3Image UI component has a built-in method called ***onImageLoad*** which provides in its invocation the full URL of any image uploaded. We will make use of this built-in function to persist our image URLs out to Cognito.

1. Replace the existing ***onImageLoad*** function with the following code:

    ```javascript
    async onImageLoad(url) {
        if (!this.state.user.getSession) { return };
        console.log('Profile Picture URL:', url);
        try {
            let result = await Auth.updateUserAttributes(this.state.user, {
                'picture': this.state.image_key
            });
            console.log(result);
        } catch (ex) {
            console.error('Attribute update error:', ex);
        }
    }
    ```
1. Now with this new method in place, upload a new photo after logging into Wild Rydes then close your browser. Open a new window and try logging in again. Your photo should load as it did previously.