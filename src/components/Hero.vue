<template>
  <div class="row mt-5">
    <div class="col align-self-center">
      <h2>
        <strong>Delicious Foods Menu,</strong> <br />
        in Your Gadget
      </h2>
      <p>Easily select and order your favorite foods</p>
      <router-link to="/">
        <button class="btn order-now">
          Order Now
          <b-icon-arrow-right-circle class="ml-2"></b-icon-arrow-right-circle>
        </button>
      </router-link>
    </div>
    <div class="col">
      <img
        src="../assets/images/hero.svg"
        alt="Hero Section Image"
        width="100%"
      />
    </div>
  </div>
</template>

<script>
export default {
  name: "Hero",
};
</script>

<style>
</style>