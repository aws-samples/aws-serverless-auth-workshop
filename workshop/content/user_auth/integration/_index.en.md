+++
title = "Integrating app with Cognito"
weight = 25
+++

Now that you've created and configured your Cognito User Pool and Identity Pool, you need to configure your application to integrate to Amazon Cognito so it can store user profiles and enable sign-up and sign-in.

### High-Level Instructions

You will import the [AWS Amplify](https://aws-amplify.github.io/) JavaScript library into the project then add sign-up and sign-in utility classes to integrate with our existing UI and front-end components.

You'll need to complete the implementation of the onSubmitForm and onSubmitVerification methods within the ***/website/src/auth/SignIn.js*** file, as well as the methods of the same name within the ***/website/src/auth/SignUp.js*** file. Finally, you'll need to complete the implementation of a method to check whether the user is authenticated within the ***/website/src/index.js*** page.

{{% expand "Step-by-step instructions (expand for details)" %}}

1. Before using any AWS Amplify modules, we first need to configure Amplify to use our newly created Cognito resources by updating **/website/src/amplify-config.js**.

2. After opening this file in your Cloud9 IDE editor, copy the following parameter values from your previous scratchpad into the config value parameter placeholders:
  * `identityPoolId`
  * `region`
  * `userPoolId`
  * `userPoolWebClientId`
  
  > Be sure to fill in the '' blanks with your config values. You do not need to modify the example values shown in the comments as they are just for reference and not leveraged by your application.

3. **Save your changes** to the Amplify config file so your new settings take effect. Any unsaved changes to a file are indicated by a dot icon in the tab of the editor so if you see a gray dot next to the file name, you may have forgotten to save.

4. Next, edit the ***website/src/index.js*** file to add the following lines to the **top of the file (but below all the other imports)** to configure Amplify then save your changes:

    ```javascript
    import Amplify from 'aws-amplify';
    import awsConfig from './amplify-config';

    Amplify.configure(awsConfig);
    ```
   
    After making these changes, your imports should be in the following order:
    
    ```javascript
    import React from 'react';
    import ReactDOM from 'react-dom';
    import { BrowserRouter, Redirect, Route, Switch } from 'react-router-dom';
    import { Home, FAQ, Investors, MainApp, Unicorns, Profile } from './pages';
    import { SignIn, SignUp } from './auth';
    import 'normalize.css';
   
    import Amplify from 'aws-amplify';
    import awsConfig from './amplify-config';
   
    Amplify.configure(awsConfig);

    const isAuthenticated = () => false;
    ```
   
5. **Save your changes** to the ***website/src/index.js*** file.

6. Next, we need to ensure our application evaluates the user's authenticated state. In the same ***/website/src/index.js*** file, find and replace the **isAuthenticated method** with the code below to use our Amplify library's built-in user session to check this status.

    ```javascript
    const isAuthenticated = () => Amplify.Auth.User !== null;
    ```
   
7. **Save your changes** to the ***/website/src/index.js*** file.

8. Now that we've imported the Amplify and configured the Amplify library, we need to update our application's code to sign-up users using Amplify and Cognito User Pools by finding and replacing the following methods within the ***/website/src/auth/SignUp.js*** file with the following code. 

    > You only need to replace these two methods. The rest of the SignUp.js file should not be modified.
                                                                                                                                                                                                                                                                                                       
    > The onSubmitForm method handles the event when the registration form is submitted. This calls the Auth.signUp method from the AWS Amplify library which registers the user with your Cognito User Pool.
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       
    > The onSubmitVerification method handles the event when the verification code entry form is submitted after the initial registration request. This calls the Auth.confirmSignUp method from the AWS Amplify library which confirms the user registration within your Cognito User Pool.                                                                                                                                                                                                                                                                                                       

    ```javascript
    async onSubmitForm(e) {
      e.preventDefault();
      try {
          const params = {
              username: this.state.email.replace(/[@.]/g, '|'),
              password: this.state.password,
              attributes: {
                  email: this.state.email,
                  phone_number: this.state.phone
              },
              validationData: []
          };
          const data = await Auth.signUp(params);
          console.log(data);
          this.setState({ stage: 1 });
      } catch (err) {
        if (err === "No userPool") {
          // User pool not defined in Amplify config file
          console.error("User Pool not defined");
          alert("User Pool not defined. Amplify config must be updated with user pool config");
        } else if (err.message === "User already exists") {
            // Setting state to allow user to proceed to enter verification code
            this.setState({ stage: 1 });
        } else {
            if (err.message.indexOf("phone number format") >= 0) {err.message = "Invalid phone number format. Must include country code. Example: +14252345678"}
            alert(err.message);
            console.error("Exception from Auth.signUp: ", err);
            this.setState({ stage: 0, email: '', password: '', confirm: '' });
        }
      }
    }

    async onSubmitVerification(e) {
        e.preventDefault();
        try {
          const data = await Auth.confirmSignUp(
              this.state.email.replace(/[@.]/g, '|'),
              this.state.code
          );
          console.log(data);
          // Go to the sign in page
          this.props.history.replace('/signin');
        } catch (err) {
          alert(err.message);
          console.error("Exception from Auth.confirmSignUp: ", err);
        }
    }
    ```
   
9. **Save your changes** to the ***/website/src/auth/SignUp.js*** file.

10. You additionally need to integrate the sign-in capability to use AWS Amplify and Cognito by finding and replacing the following methods within the **/website/src/auth/SignIn.js** file with the code below.

    > You only need to replace these two methods. The rest of the SignIn.js file should not be modified.
    
    > The onSubmitForm method initiates the signin request with your Cognito User Pool by invoking the Auth.signIn method from AWS Amplify then sets the local state appropriately to indicate the user has signed in successfully.                                                                                                                                                                                                                  
                                                                                                                                                                                                                     
    > The onSubmitVerification method is used to submit a verification code whenever multi-factor authentication is required to authenticate. For this workshop, this method will not be invoked since you did not require multi-factor authentication earlier when configuring your Cognito User Pool.
    
    ```javascript
    async onSubmitForm(e) {
        e.preventDefault();
        try {
            const userObject = await Auth.signIn(
              this.state.email.replace(/[@.]/g, '|'),
              this.state.password
            );
            console.log('userObject', userObject);
            if (userObject.challengeName) {
              // Auth challenges are pending prior to token issuance
              this.setState({ userObject, stage: 1 });
            } else {
              // No remaining auth challenges need to be satisfied
              const session = await Auth.currentSession();
              // console.log('Cognito User Access Token:', session.getAccessToken().getJwtToken());
              console.log('Cognito User Identity Token:', session.getIdToken().getJwtToken());
              // console.log('Cognito User Refresh Token', session.getRefreshToken().getToken());
              this.setState({ stage: 0, email: '', password: '', code: '' });
              this.props.history.replace('/app');
            }
        } catch (err) {
            alert(err.message);
            console.error('Auth.signIn(): ', err);
        }
    }

    async onSubmitVerification(e) {
        e.preventDefault();
        try {
          const data = await Auth.confirmSignIn(
            this.state.userObject,
            this.state.code
          );
          console.log('Cognito User Data:', data);
          const session = await Auth.currentSession();
          // console.log('Cognito User Access Token:', session.getAccessToken().getJwtToken());
          console.log('Cognito User Identity Token:', session.getIdToken().getJwtToken());
          // console.log('Cognito User Refresh Token', session.getRefreshToken().getToken());
          this.setState({ stage: 0, email: '', password: '', code: '' });
          this.props.history.replace('/app');
        } catch (err) {
          alert(err.message);
          console.error('Auth.confirmSignIn(): ', err);
        }
    }
    ``` 

11. **Save your changes** to the ***/website/src/auth/SignIn.js*** file.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       
