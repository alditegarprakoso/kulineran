<template>
  <div class="FoodDetail">
    <Navbar />

    <div class="container">
      <div class="row mt-3 mb-3">
        <div class="col">
          <nav class="breadcrumb">
            <a class="breadcrumb-item" href="/foods">Foods</a>
            <span class="breadcrumb-item active">Food Detail</span>
          </nav>
        </div>
      </div>

      <div class="row">
        <div class="col-md-6">
          <img
            :src="'../assets/images/foods/' + product.gambar"
            class="img-fluid shadow rounded"
            height="300"
          />
        </div>
        <div class="col-md-6">
          <h2>
            <strong>{{ product.nama }}</strong>
          </h2>
          <hr />
          <h5>
            Harga: <strong>Rp. {{ product.harga }}</strong>
          </h5>
          <form action="" class="mt-3">
            <div class="form-group">
              <label for="jumlah">Jumlah Pesanan</label>
              <input
                type="text"
                name="jumlah"
                id="jumlah"
                class="form-control"
              />
            </div>
            <div class="form-group">
              <label for="keterangan">Keterangan Pesanan</label>
              <textarea
                class="form-control"
                name="keterangan"
                id="keterangan"
                rows="3"
                placeholder="Tambahkan keterangan untuk pesanan seperti pedas, sedang, atau keterangan lainnya ... (Opsional)"
              ></textarea>
            </div>
            <button type="submit" class="btn btn-sm order-now">
              <b-icon-cart class="mr-2"></b-icon-cart> Order
            </button>
          </form>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Navbar from "@/components/Navbar.vue";
import axios from "axios";

export default {
  name: "FoodDetail",
  components: {
    Navbar,
  },
  data() {
    return {
      product: {},
    };
  },
  methods: {
    setProduct(data) {
      this.product = data;
    },
  },
  mounted() {
    axios
      .get("http://localhost:3000/products/" + this.$route.params.id)
      .then((response) => this.setProduct(response.data))
      .catch((error) => console.log(error));
  },
};
</script>

<style>
</style>