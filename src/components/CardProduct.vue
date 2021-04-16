<template>
  <div class="card h-100 shadow">
    <img
      :src="'assets/images/foods/' + product.gambar"
      class="card-img-top"
      alt="..."
      height="200"
    />
    <div class="card-body">
      <h5 class="card-title">
        <strong>{{ product.nama }}</strong>
      </h5>
      <p class="card-text">
        Price: <strong>Rp. {{ product.harga }}</strong>
      </p>
    </div>
    <router-link :to="'/foods/' + product.id" class="btn order-now"
      >Order</router-link
    >
  </div>
</template>

<script>
export default {
  name: "CardProduct",
  props: ["product"],
};
</script>

<style>
</style>