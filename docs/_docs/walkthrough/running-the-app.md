---
title: Running the app
category: Walkthrough
order: 2
---
Before you can use the app, you need to complete the following steps.

1. Create a tunnel to your localhost by running `yarn lt --port 3000 --subdomain checkout-example`.
  This tunnel lets the app handle the redirect to the success, failure, or cancellation page.
1. Build and serve the app by running `yarn dev`.
  _The app is built in development mode. Wait for a message similar to the following to appear in your terminal:_
  ```
  Waiting for file changes
  Memory usage: 606 MB (RSS: 736 MB)
  Listening on: http://localhost:3000
  ```
  Next, follow the steps in [Using the app](../using-the-app/).