//
<template>
  <div class="wrapper">
    <div class="cart">
      <div class="cart-header">
        <h4>Cart ({{ cartItems.length }} items)</h4>
        <img src="../assets/sinus-logo.svg" />
      </div>

      <CartItem
        @forceRerender="forceRerender"
        v-for="item in cartItems"
        :key="`${componentKey}-${item._id}`"
        :product="item"
      />
    </div>
    <div class="total-price">
      <p class="total-lable">Total:</p>
      <div class="price-container">
        <div class="item-total">
          <p class="sek-lable">Item total:</p>
          <p class="price">
            <strong>{{ totalPrice ? `${totalPrice} KR` : "" }}</strong>
          </p>
        </div>

        <div class="shipping-wrapper">
          <p class="shipping">Shipping:</p>
          <p class="free">FREE</p>
        </div>
        <hr />
      </div>

      <div>
        <input class="details" type="text" placeholder="Enter Discount Code" />
        <a @click="addOrder" class="btn"> Go to checkout</a>
      </div>
    </div>
  </div>
</template>
<script>
import CartItem from "@/components/ShoppingCart/CartItem.vue";
export default {
  name: "Cart",
  components: { CartItem },
  data() {
    return {
      showModal: false,
      componentKey: 0,
    };
  },
  computed: {
    cartItems() {
      return this.$store.getters.getOrderItems;
    },
    totalPrice() {
      return this.$store.getters.getTotalPrice;
    },
  },
  methods: {
    addOrder() {
      this.$router.push("/MakeOrder");
    },

    getUser() {
      this.$store.dispatch("getUser");
    },

    forceRerender() {
      this.componentKey += 1;
    },
  },
};
</script>

<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Bebas+Neue&family=Lato:wght@300;400;700&display=swap");
.wrapper {
  margin: 160px auto;
  display: flex;
  justify-content: space-evenly;
  width: 85%;
  min-width: 350px;
  max-width: 1440px;
}

.cart {
  width: 60%;
}

.cart-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0 20px;
  background: #9199a5;
  height: 102px;
  box-shadow: 0 6px 6px 0 rgba(0, 0, 0, 0.256);
}

h4 {
  font-weight: 400;
  font-family: "Lato", sans-serif;
  font-size: 30px;
  color: #fff;
}

.cart-header img {
  object-fit: cover;
  width: 20%;
}
.total-price {
  padding: 0 25px;
  width: 30%;
  height: 450px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  background-color: whitesmoke;
  box-shadow: 0 2.8px 2.2px rgba(0, 0, 0, 0.034),
    0 6.7px 5.3px rgba(0, 0, 0, 0.048), 0 12.5px 10px rgba(0, 0, 0, 0.06),
    0 22.3px 17.9px rgba(0, 0, 0, 0.072), 0 41.8px 33.4px rgba(0, 0, 0, 0.086),
    0 100px 80px rgba(0, 0, 0, 0.12);
}

.total-lable {
  color: #3c4858;
  padding-top: 30px;
  font-size: 30px;
  font-family: "Montserrat", sans-serif;
}

.item-total,
.shipping-wrapper {
  font-family: "Montserrat", sans-serif;
  display: flex;
  justify-content: space-between;
  margin: 30px 0;
  align-items: center;
  color: #000;
  font-size: 18px;
}

.btn {
  display: flex;
  justify-content: center;
  align-items: center;
  cursor: pointer;
  font-family: "Lato", sans-serif;
  font-size: 1.2rem;
  text-transform: uppercase;
  padding: 10px 0;
  font-weight: 500;
  color: #fbfbfb;
  margin: 30px 0;
  background-color: #5eb593;
  box-shadow: 0px 6px 4px rgba(0, 0, 0, 0.15);
}
.btn:hover {
  background: #000;
  color: #fff;
}
</style>
