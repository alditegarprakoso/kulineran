<template>
  <div class="home">
    <div class="container">
      <Navbar />
      <Hero />

      <div class="row mt-5 mb-3">
        <div class="col">
          <h3>Best <strong>Foods</strong></h3>
        </div>
        <div class="col">
          <router-link to="/foods" class="best-foods float-right">
            <p>
              <strong
                >See All <b-icon-arrow-right></b-icon-arrow-right>
              </strong>
            </p>
          </router-link>
        </div>
      </div>

      <div class="row row-cols-1 row-cols-md-3">
        <div class="col mb-4" v-for="product in products" :key="product.id">
          <CardProduct :product="product" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import Navbar from "@/components/Navbar.vue";
import Hero from "@/components/Hero.vue";
import CardProduct from "@/components/CardProduct.vue";
import axios from "axios";

export default {
  name: "Home",
  components: {
    Navbar,
    Hero,
    CardProduct,
  },
  data() {
    return {
      products: [],
    };
  },
  methods: {
    setProducts(data) {
      this.products = data;
    },
  },
  mounted() {
    axios
      .get("http://localhost:3000/best-products")
      .then((response) => this.setProducts(response.data))
      .catch((error) => console.log("Gagal : ", error));
  },
};
</script>