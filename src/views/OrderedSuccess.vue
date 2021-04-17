<template>
  <div class="ordered-success">
    <div class="container">
      <Navbar />

      <div class="row justify-content-center text-center mt-4">
        <div class="col">
          <h2>
            <strong>Ordered</strong>
            <strong style="color: #289672"> Successfully</strong>
          </h2>
          <p>Your order is being processed, please wait a moment</p>
          <img :src="'../assets/images/checkout.svg'" height="330" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Navbar from "@/components/Navbar.vue";

export default {
  name: "OrderedSuccess",
  components: {
    Navbar,
  },
};
</script>

<style>
</style>