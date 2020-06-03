+++
title = "Solution Architecture"
weight = 21
+++

The architecture for this module is very straightforward. All of your static web content including HTML, CSS, JavaScript, images and other files will be served locally from your Cloud9 workspace. As you make changes to the website application code, all changes will be automatically updated and shown in your browser via live reload capabilities.

For this module, we will be creating a Cognito User Pool as our secure user directory then configuring our application to use the AWS Amplify library to easily integrate Amazon Cognito into our application.

![Module 1 Architecture](../images/wildrydes-module1-architecture.png)

### Implementation Overview

Each of the following sections provides an implementation overview and detailed, step-by-step instructions. The high-level overview should provide context for you to complete the implementation yourself if you're comfortable with the AWS Management Console and are comfortable exploring the services and documentation yourself without following a walkthrough.

If you're using the latest version of the Chrome, Firefox, or Safari web browsers the step-by-step instructions won't be visible until you expand the section.

