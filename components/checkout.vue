<template>
  <button @click="startCheckoutSession" class="button--green">Pay</button>
</template>

<script>
export default {
  methods: {
    async startCheckoutSession() {
      let authKey = 'Bearer ' + this.$config.apiKey;
      let mId = this.$config.mId;
      this.$axios.setHeader('Authorization', authKey);
      this.$axios.setHeader('X-Clover-Merchant-ID', mId);
      try {
        let checkoutSession = await this.$axios.$post('https://sandbox.dev.clover.com/invoicingcheckoutservice/v1/checkouts', 
        {

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
          "customer": {
            "email": "email@example.com",
            "firstName" : "Example",
            "lastName": "Customer",
            "phoneNumber": "223-555-0002"
          }
        }
      );
      window.location.href = checkoutSession.href
      } catch (error) {
        window.alert(error)
      }
    },
  },
};
</script>