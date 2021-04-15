<template>
  <div class="hero" style="margin-bottom: 115px">
    <!-- Hero Section for Desktop Display -->
    <div class="d-none d-md-block" style="margin-top: 65px">
      <div class="row mt-5">
        <div class="col-md-6 align-self-center">
          <h2>
            <strong class="hero-p">Delicious Foods Menu,</strong> <br />
            in Your Gadget
          </h2>
          <p>Easily select and order your favorite foods</p>
          <router-link to="/foods" class="btn order-now">
            Order Now
            <b-icon-arrow-right-circle class="ml-2"></b-icon-arrow-right-circle>
          </router-link>
        </div>
        <div class="col-md-6">
          <img
            :src="'assets/images/hero.svg'"
            alt="Hero Section Image"
            width="100%"
          />
        </div>
      </div>
    </div>
    <!-- Hero Section for Desktop Display -->

    <!-- Hero Section for Mobile Display -->
    <div class="d-sm-block d-md-none" style="margin-top: 65px">
      <div class="row mt-4 text-center">
        <div class="col-md-6 mb-4">
          <img
            :src="'assets/images/hero.svg'"
            alt="Hero Section Image"
            width="85%"
          />
        </div>
        <div class="col-md-6 align-self-center">
          <h2>
            <strong class="hero-p">Delicious Foods Menu,</strong> <br />
            in Your Gadget
          </h2>
          <p>Easily select and order your favorite foods</p>
          <router-link to="/" class="btn order-now">
            Order Now
            <b-icon-arrow-right-circle class="ml-2"></b-icon-arrow-right-circle>
          </router-link>
        </div>
      </div>
    </div>

    <!-- Hero Section for Mobile Display -->
  </div>
</template>

<script>
export default {
  name: "Hero",
};
</script>

<style>
</style>