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
          <form action="" class="mt-3" v-on:submit.prevent>
            <div class="form-group">
              <label for="jumlah">Jumlah Pesanan</label>
              <input
                type="text"
                name="jumlah"
                id="jumlah"
                class="form-control"
                v-model="order.jumlah_pemesanan"
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
                v-model="order.keterangan"
              ></textarea>
            </div>
            <button type="submit" class="btn btn-sm order-now" @click="booking">
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
      order: {},
    };
  },
  methods: {
    setProduct(data) {
      this.product = data;
    },
    booking() {
      if (this.order.jumlah_pemesanan) {
        this.order.products = this.product;
        axios
          .post("http://localhost:3000/keranjangs", this.order)
          .then(() => {
            this.$route.push({ path: "/cart" });
            this.$toast.success("Success Booking.", {
              type: "success",
              position: "top-right",
              duration: "2500",
              dismissible: true,
            });
          })
          .catch((error) => {
            console.log(error);
          });
      } else {
        this.$toast.error("Booking failed.", {
          type: "error",
          position: "top-right",
          duration: "2500",
          dismissible: true,
        });
      }
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