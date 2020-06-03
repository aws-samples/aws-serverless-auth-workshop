+++
title = "Validating sign-up and sign-in"
weight = 26
+++

Now that you have integrated our Amplify code into our application, you need to test the site to see that authentication is working end-to-end.

### High-Level Instructions

Return to your browser tab where you started your Wild Rydes application earlier after popping out from the Cloud9 IDE once in preview mode. This page automatically refreshes after you save any code changes so should now reflect all of your changes and be ready for testing.

Visit the ***/register*** path to sign-up as a new user, providing a valid phone number with `+country_code` first preceeding the number. For a US-based phone number, an example would be `+14251234567`. You should then see that a verification message is sent with a one-time code upon registering, which is required before you're able to sign-in.

After signing up as a new user, sign-in with the same user at the ***/signin*** path. If the page loads a map, sign-in was successful and you have successfully integrated Cognito for app authentication.

{{% expand "Step-by-step instructions (expand for details)" %}}

1. Visit `/register` path of your Cloud9's website to go to the registration page.

2. Input your e-mail address, phone number with `+country_code` first preceeding the number, as well as your password twice. For a US-based phone number, an example would be `+14251234567`. 

    > Your password must include 8 characters, including uppercase and lowercase characters, and at least 1 number and 1 special character.

3. Choose **Let's Ryde** to submit registration.

4. On the verify e-mail screen, enter the one-time code sent to your e-mail address provided then choose **Verify**.

    > Be sure to check your spam folder for the e-mail with your verification code if you do not see it in your inbox.

5. Assuming no errors were encountered, you will be redirected to the Sign-in screen. Now, re-enter the same e-mail address and password you chose at registration.

6. If the page then loads a map, sign-in was successful and you have successfully integrated Cognito for app authentication.

7. Optionally, you may scroll down beyond the map to copy your user's identity token and decode it by pasting it into the 'encoded' input box at [JWT.io](http://jwt.io/). You will see all of your user's attributes are encoded within the token, along with other standard attributes such as the time the token was issued, the time the token expires, the user's unique ID, and more.

