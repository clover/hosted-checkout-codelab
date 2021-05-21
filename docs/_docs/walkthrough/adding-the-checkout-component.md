---
title: Adding the checkout component
category: Walkthrough
order: 1
---
To start the checkout process, you need to send data about the transaction
to the `/checkouts` endpoint.
For this app, we'll create a Nuxt.js component to include on the index page.
When a user clicks this button component, the following actions occur:

1. The merchant's API key and ID are retrieved from the .env file.
1. The key and ID values are assigned to the relevant HTTP headers.
1. A checkout session is created.
1. The returned session data is used to redirect the user to the checkout page.

## Create the component and add a button

1. Create a new file in the `components` directory named `checkout.vue`.
1. Open the new file in your editor.

    The first part of the component is the `<template>`, a container for the `<button>`.

1. Add the following snippet to the file:

    ```html
    <template>
      <button class="button--green">Pay</button>
    </template>
    ```

    If you run the app at this point, the button appears but there is no action tied to it. To make it usable, we need to add code to initiate a checkout session.

## Add the scripting code

1. In `checkout.vue`, add a `<script>` following the `<template>`.

    ```html
    ...
    </template>
  
    <script>
    
    </script>
    ```

1. In the `<script>`, add an empty async method named `startCheckoutSession()`.

    ```js
    export default {
      methods: {
        async startCheckoutSession() {
          
        },
      },
    };
    ```

1. The checkout session request must be authenticated with the merchant's hosted checkout API key. Add a variable named `authKey` to store this key.

    ```js
    async startCheckoutSession() {
      let authKey = 'Bearer ' + this.$config.apiKey;

    },
    ```

1. The session request also requires the Clover merchant identifier (mId). Add another variable named `mId` for this value.

    ```js
    async startCheckoutSession() {
      let authKey = 'Bearer ' + this.$config.apiKey;
      let mId = this.$config.mId;
    },
    ```

1. Set the HTTP headers using the variables created in the previous steps.

    ```js 
    ...
    let mId = this.$config.mId;
    this.$axios.setHeader('Authorization', authKey);
    this.$axios.setHeader('X-Clover-Merchant-ID', mId);
    ```

1. Add a `try/catch` statement with a window alert to display any error messages returned by the API.

    ```js
    try {
        
      } catch (error) {
        window.alert(error);
    };
    ```

1. In the `try` block, set up the POST request by passing the `/invoicingcheckoutservice/v1/checkouts` as the first parameter.

    ```js
    let checkoutSession = await this.$axios.$post('https://sandbox.dev.clover.com/invoicingcheckoutservice/v1/checkouts');
    ```

1. For the second parameter, add a JSON request body including the `customer` and `shoppingCart` objects.

    ```js
    let checkoutSession = await this.$axios.$post('https://sandbox.dev.clover.com/invoicingcheckoutservice/v1/checkouts',
      {
        "customer": {
          "email": "email@example.com",
          "firstName" : "Example",
          "lastName": "Customer",
          "phoneNumber": "223-555-0002"
        },
        "shoppingCart": {
          "lineItems": [
            {
              "name": "Apple",
              "unitQty": 1,
              "price": 100
            },
            {
              "name": "Orange",
              "unitQty": 2,
              "price": 75
            }
          ]
        },
      },
    );
    ```

1. Once the endpoint returns a session ID, the user needs to be redirected to the checkout page. Do this by setting the `window.location.href` property to the value of the `href` returned by the `/checkouts` endpoint.
    ```js
    try {
      let checkoutSession = await this.$axios.$post(
      ...
    );
    window.location.href = checkoutSession.href;
    } catch (error) {
        window.alert(error);
    }
    ```

    _The `<script>` now has the code required to complete a checkout session._
1. Add a click event listener to the `<button>` that will start the checkout process when the **Pay** button is clicked. The value of the `@click` attribute is the method name to invoke (`startCheckoutSession`).
    ```html
    <button @click="startCheckoutSession"class=" button--grey">Pay</button>
    ```

You can now follow the steps in [Running the app](../running-the-app/) to build and serve the app locally.
