+++
title = "Setup Cloud9 Workspace"
weight = 14
+++

In the ***bash*** terminal in Cloud9, you can run AWS CLI commands just like you would on your local computer. Verify that your user is logged in by running the following: 
```plaintext
aws sts get-caller-identity
```

You should see output indicating your account and user information: 

```JSON
{
  "Account": "123456789012",
  "UserId": "AKIAI44QH8DHBEXAMPLE",
  "Arn": "arn:aws:iam::123456789012:user/Alice"
}
```

Keep your AWS Cloud9 IDE opened in a tab throughout this workshop as you'll be using it for most activities.

### Download Workshop Code

Download the WildRydes website artifacts to your Cloud9 IDE environment by running the following command in the Cloud9 terminal window:
    
```plaintext
curl -O {{% siteparam "artifactUrlPrefix" %}}/website.tar.gz
tar xvf website.tar.gz
```

### Initialize your developer workspace

1. Run the following commands to upgrade your Node.js version to the latest version of Node.js 10. The [AWS Amplify](https://aws-amplify.github.io/) Javascript library which we will be using requires Node.js 10 or higher.

    ```plaintext
    nvm i 10
    nvm alias default 10
    ```

2. Install the yarn package manager and website dependencies by running the following commands:

    ```plaintext 
    npm install -g yarn
    cd ~/environment/website/
    yarn install
    ```

{{% notice tip %}}
Keep an open scratch pad in Cloud9 or a text editor on your local computer for notes. When the step-by-step directions tell you to note something such as an ID or Amazon Resource Name (ARN), copy and paste that into the scratch pad tab.
{{% /notice %}}
    
