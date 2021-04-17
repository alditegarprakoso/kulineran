<template>
  <div class="Cart">
    <div class="container">
      <Navbar :updateCart="keranjangs" />

      <div class="row mt-3 mb-3">
        <div class="col">
          <nav class="breadcrumb">
            <a class="breadcrumb-item" href="/foods">Foods</a>
            <span class="breadcrumb-item active">Cart</span>
          </nav>
        </div>
      </div>

      <div class="row mb-4">
        <div class="col">
          <h2>
            <strong>My</strong> <strong style="color: #289672">Cart</strong>
          </h2>
        </div>
      </div>

      <div class="row">
        <div class="col">
          <div class="table-responsive">
            <table class="table text-center">
              <thead>
                <tr>
                  <th>No.</th>
                  <th>Gambar</th>
                  <th>Makanan</th>
                  <th>Keterangan</th>
                  <th>Jumlah Pesanan</th>
                  <th>Harga</th>
                  <th>Total Harga</th>
                  <th>Action</th>
                </tr>
              </thead>
              <tbody>
                <tr
                  v-for="(keranjang, index) in keranjangs"
                  :key="keranjang.id"
                >
                  <td scope="row">{{ index + 1 }}</td>
                  <td>
                    <img
                      :src="
                        '../assets/images/foods/' + keranjang.products.gambar
                      "
                      height="150"
                      class="rounded"
                    />
                  </td>
                  <td>{{ keranjang.products.nama }}</td>
                  <td>
                    {{ keranjang.keterangan ? keranjang.keterangan : "-" }}
                  </td>
                  <td>{{ keranjang.jumlah_pemesanan }}</td>
                  <td>Rp. {{ keranjang.products.harga }}</td>
                  <td>
                    <strong>
                      Rp.
                      {{ keranjang.totalHarga }}
                    </strong>
                  </td>
                  <td>
                    <button
                      @click="cancel(keranjang.id)"
                      class="btn btn-danger btn-sm"
                    >
                      Cancel <b-icon-trash></b-icon-trash>
                    </button>
                  </td>
                </tr>

                <tr>
                  <td colspan="6" align="right">
                    <strong>Total Harga:</strong>
                  </td>
                  <td>
                    <strong>Rp. {{ total }}</strong>
                  </td>
                </tr>
              </tbody>
            </table>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Navbar from "@/components/Navbar.vue";
import axios from "axios";

export default {
  name: "Cart",
  components: {
    Navbar,
  },
  data() {
    return {
      keranjangs: [],
    };
  },
  methods: {
    setKeranjangs(data) {
      this.keranjangs = data;
    },
    cancel(id) {
      axios
        .delete("http://localhost:3000/keranjangs/" + id)
        .then(() => {
          this.$toast.success("Data deleted successfully.", {
            type: "success",
            position: "top-right",
            duration: "2500",
            dismissible: true,
          });

          // Reload Data
          axios
            .get("http://localhost:3000/keranjangs")
            .then((response) => this.setKeranjangs(response.data))
            .catch((error) => console.log(error));
        })
        .catch((error) => console.log(error));
    },
  },
  mounted() {
    axios
      .get("http://localhost:3000/keranjangs")
      .then((response) => this.setKeranjangs(response.data))
      .catch((error) => console.log(error));
  },
  computed: {
    total() {
      return this.keranjangs.reduce(function (items, data) {
        return items + data.totalHarga;
      }, 0);
    },
  },
};
</script>

<style>
</style>