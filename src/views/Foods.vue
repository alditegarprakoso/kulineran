<template>
  <div class="Foods">
    <Navbar />

    <div class="container">
      <div class="row mt-4 mb-3">
        <div class="col">
          <h2>
            <strong style="color: #289672">Foods</strong> <strong>List</strong>
          </h2>
        </div>
      </div>

      <div class="row mb-4">
        <div class="col">
          <div class="form-group">
            <input
              v-model="search"
              type="text"
              name=""
              id=""
              class="form-control"
              placeholder="Find food..."
              @keyup="searchFood"
            />
          </div>
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
import CardProduct from "@/components/CardProduct.vue";
import axios from "axios";

export default {
  name: "Foods",
  components: {
    Navbar,
    CardProduct,
  },
  data() {
    return {
      products: [],
      search: "",
    };
  },
  methods: {
    setProducts(data) {
      this.products = data;
    },
    searchFood() {
      axios
        .get("http://localhost:3000/products?q=" + this.search)
        .then((response) => this.setProducts(response.data))
        .catch((error) => console.log("Gagal : ", error));
    },
  },
  mounted() {
    axios
      .get("http://localhost:3000/products")
      .then((response) => this.setProducts(response.data))
      .catch((error) => console.log("Gagal : ", error));
  },
};
</script>

<style>
</style>