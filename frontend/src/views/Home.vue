<template>
  <div class="landing-wrapper">
    <div class="landing-top">
      <section class="top-products">
        <h1>TOP-SELLING SKATEBOARDS</h1>
        <div class="top-img-wrapper">
          <Product-card
            @click.native="changeRoute(product._id)"
            class="prod-card-left"
            v-for="product in products.slice(0, 1)"
            :key="product._id"
            :product="product"
          />

          <Product-card
            @click.native="changeRoute(product._id)"
            class="prod-card-right"
            v-for="(product, index) in products.slice(1, 2)"
            :key="index"
            :product="product"
          />
        </div>
        <div class="all-products">
          <h3>VIEW ALL PRODUCTS</h3>
          <img class="arrow" src="@/assets/arrow-double.svg" />
        </div>
      </section>
    </div>

    <div class="landing-bottom">
      <section class="bottom-products">
        <h2>ALL PRODUCTS</h2>
        <!-- <p>Dropdown menu</p> -->
      </section>

      <section class="product-grid-container">
        <ProductCard
          @click.native="changeRoute(product._id)"
          v-for="(product, index) in products"
          :key="index"
          :product="product"
        />
      </section>
      <div class="progress-bar">
        <p>Showing 9 out of 30 products</p>
        <button>SHOW MORE</button>
      </div>
    </div>
  </div>
</template>

<script>
import ProductCard from "@/components/Product/ProductCard.vue";
export default {
  components: { ProductCard },

  computed: {
    products() {
      return this.$store.getters.getProducts;
    },
  },

  methods: {
    changeRoute(id) {
      this.$router.push(`/singleproduct/${id}`);
    },
  },
};
</script>

<style scoped>
* {
  color: black;
}

.landing-wrapper {
  margin-top: 75px;
}

.landing-top {
  height: 862px;
  width: 1440px;
  background-image: url("../assets/BG image landing.jpg");
  margin-top: 20px;
}

.top-products h1{
  display: flex;
  justify-content: center;
}

.landing-top h1,
h3 {
  color: white;
  font-family: "Bebas Neue";
  font-size: 35px;
  padding: 20px;
  
}

.all-products {
  display: flex;
  justify-content: center;
}

.top-img-wrapper {
  display: flex;
  flex-direction: row;
  justify-content: center;
  gap: 30px;
}

.prod-card-left,
.prod-card-right {
  height: 526px;
  width: 419px;
  border-radius: 10px;
  overflow-y: auto;
  box-shadow: 0 2.8px 2.2px rgba(0, 0, 0, 0.034),
    0 6.7px 5.3px rgba(0, 0, 0, 0.048), 0 12.5px 10px rgba(0, 0, 0, 0.06),
    0 22.3px 17.9px rgba(0, 0, 0, 0.072), 0 41.8px 33.4px rgba(0, 0, 0, 0.086),
    0 100px 80px rgba(0, 0, 0, 0.12);
  margin-top: 2rem;
  padding: 2rem;

  width: 400px;
  background-color: whitesmoke;
}

.landing-bottom {
  height: 1724px;
  width: 1440px;
  background-color: #3c4858;
}

.landing-bottom h2 {
  padding: 15px;
  font-family: "Bebas Neue";
}

.product-grid-container {
  display: grid;
  gap: 20px;
  grid-template-columns: 270px 270px 270px;
  grid-auto-rows: 350px;
  align-items: center;
  justify-content: center;
  border: none;
}

.bottom-products h2,
p {
  color: white;
  display: flex;
  justify-content: center;
}

.product-grid-container > p {
  height: 327px;
  width: 245px;
  background-color: white;
}
button {
  height: 43px;
  width: 332px;
  border-radius: 5px 0px 0px 5px;
  background-color: #3c8af1;
}

.progress-bar {
  display: flex;
  flex-direction: column;
  /* justify-content: center; */
  margin-top: 10px;
  margin-bottom: 10px;
  gap: 5px;
  align-items: center;
}




</style>
