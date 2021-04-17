<template>
  <div>
    <b-navbar toggleable="lg">
      <b-navbar-brand href="/"
        ><strong style="color: #289672">Kulineran</strong></b-navbar-brand
      >

      <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

      <b-collapse id="nav-collapse" is-nav>
        <b-navbar-nav>
          <b-nav-item>
            <router-link class="nav-link" to="/">Home</router-link>
          </b-nav-item>
          <b-nav-item>
            <router-link class="nav-link" to="/foods">Foods</router-link>
          </b-nav-item>
        </b-navbar-nav>

        <!-- Right aligned nav items -->
        <b-navbar-nav class="ml-auto">
          <b-nav-item>
            <router-link class="nav-link" to="/cart"
              >Cart
              <b-icon-cart class="mr-2"></b-icon-cart>
              <span class="badge badge-success foods-cart">
                {{ updateCart ? updateCart.length : jumlah_pesanan.length }}
              </span>
            </router-link>
          </b-nav-item>
        </b-navbar-nav>
      </b-collapse>
    </b-navbar>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "Navbar",
  data() {
    return {
      jumlah_pesanan: [],
    };
  },
  props: ["updateCart"],
  methods: {
    setJumlah(data) {
      this.jumlah_pesanan = data;
    },
  },
  mounted() {
    axios
      .get("http://localhost:3000/keranjangs")
      .then((response) => this.setJumlah(response.data))
      .catch((error) => console.log(error));
  },
};
</script>

<style>
</style>