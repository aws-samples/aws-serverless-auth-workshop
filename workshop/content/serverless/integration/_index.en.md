+++
title = "Integrate API into Wild Rydes"
weight = 33
+++

Now that you have created our Serverless API, you need to update your Wild Rydes web application to integrate with it. You will leverage the AWS Amplify client library to make API calls and inject security seamlessly to support your authentication and authorization scenarios.

### High-Level Instructions

First, expand your **amplify-config.js** file to store your new API Gateway endpoint. Next, within **MainApp.js** under pages, enable the **hasAPI** method by uncommenting its functionality. Additionally, update the **getData** method to capture the latitude and longitude selected on the map and send to the API as a PickupLocation object including both the latitude and longitude.

{{% expand "Step-by-step instructions (expand for details)" %}}

1. First, you need to update the **/website/src/amplify-config.js** file to include your new API Gateway endpoint. Store the endpoint including the /prod at the end in the endpoint property under the **WildRydesAPI** section.

    > Do not change the name `WildRydesAPI` in this configuration file or later functionality in the workshop will not work. An example of the API configuration portion of the amplify-config file after updating the configuration properly is shown below:

    ```javascript
    API: {
        endpoints: [
            {
                name: 'WildRydesAPI',
                endpoint: 'https://1ngrgqjt6c.execute-api.us-east-1.amazonaws.com/prod',
                region: 'us-east-1'
            }
        ]
    },
    ```

1. Next, you need to enable the hasAPI method by uncommenting its code within **/website/src/pages/MainApp.js**.

    ```javascript
    hasApi() {
        const api = awsConfig.API.endpoints.filter(v => v.endpoint !== '');
        return (typeof api !== 'undefined');
    }
    ```

1. Finally, within the same file, we will implement the API request for a ride as a POST request to our API which sends a body containing the requested latitude and longitude as the pickup location. Update the **getData()** method to be as follows:

    ```javascript
    async getData(pin) {
        const apiRequest = {
          body: {
            PickupLocation: {
              Longitude: pin.longitude,
              Latitude: pin.latitude
            }
          },
          headers: {
            'Authorization': '', // To be updated
            'Content-Type': 'application/json'
          }
        };
        console.log('API Request:', apiRequest);
        return await API.post(apiName, apiPath, apiRequest);
    }
    ```
