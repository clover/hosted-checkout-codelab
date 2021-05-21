![alt text](https://www.clover.com/assets/images/public-site/press/clover_primary_gray_rgb.png)
# Clover Hosted Checkout Codelab

A simple tutorial showing how to create a Clover hosted checkout session,
process a payment, and redirect to the merchant site. There are two ways to get started with these instructions.

* If you are using Visual Studio Code for your editor, you can step through a walkthrough of the app.
  1. Install the [CodeTour extension](https://marketplace.visualstudio.com/items?itemName=vsls-contrib.codetour)
  2. Checkout the `complete` branch
  3. Start the Codelab intro tour and walk through the codebase
  4. Run the app with `yarn dev`.
* All other readers can learn about the repo by reading the [Hosted Checkout Codelab docs](https://clover.github.io/hosted-checkout-codelab/)

## About this repo

> :triangular_flag_on_post:	IMPORTANT<br />
> The purpose of this tutorial is to teach Clover developers about the hosted checkout API. The resulting application should not be used in the production environment.

This lesson provides a Vue app bootstrapped with Nuxt.js as a starting point.
You will learn how to configure the app to interact with Clover's
hosted checkout API. This API is the simplest option for adding Clover payments
to a merchant's website. It is ideal for small businesses wanting
to quickly set up an online payment option for their customers.

There are some limitations to consider when choosing to integrate with hosted checkout.

1. A merchant's Clover inventory cannot be used with hosted checkout.
2. Refunds and voids are not available with hosted checkout. Hosted checkout provides a customer-facing payment interface, not a fully-featured payment system for merchants.

### Branches

* `main` - the current stable version of the codelab
* `complete` - a version of the codelab with all steps completed (except for the setup of the `.env` file) 

### Credits

[Edition Jekyll template](https://github.com/CloudCannon/edition-jekyll-template)

© 2021 Clover Network, Inc.
