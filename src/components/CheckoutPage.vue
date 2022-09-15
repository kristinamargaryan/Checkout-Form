<template>
  <div>
    <stripe-checkout
      ref="checkoutRef"
      mode="payment"
      :pk="publishableKey"
      :line-items="lineItems"
      :success-url="successURL"
      :cancel-url="cancelURL"
      @loading="(v) => (loading = v)"
    />
    <button @click="submit">Pay now!</button>
  </div>
</template>

<script>
import { StripeCheckout } from "@vue-stripe/vue-stripe";
export default {
  components: {
    StripeCheckout,
  },
  data() {
    this.publishableKey =
      "pk_test_51LiBcaLhhvxG1eS0UxsfoaDZ1xtIvM1PXWebI6mpDlQozSL6krUyXwaCiEKldV9bH2pFGjHeImdNrnf8EUBCYZJs009s4F2srq";
    return {
      loading: false,
      lineItems: [
        {
          price: "price_1LiCVfLhhvxG1eS09yl6cP8i", 
          quantity: 1,
        },
      ],
      successURL: "https://buy.stripe.com/test_bIYbL870L0XY8xi8ww",
      cancelURL: "http://localhost:8080/",
    };
  }, 
  methods: {
    submit() {
      window.location.href = 'https://buy.stripe.com/test_bIYbL870L0XY8xi8ww'
    },
  },
};
</script>

<style scoped>
button {
  background-color: #ea4c89;
  border-radius: 8px;
  border-style: none;
  color: #ffffff;
  cursor: pointer;
  font-size: 20px;
  height: 50px;
  margin: 0;
  padding: 10px 16px;
}
button:hover {
  background-color: #b1748b;
}
</style>
