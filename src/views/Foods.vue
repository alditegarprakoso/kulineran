<template>
  <div class="Foods">
    <Navbar />
    <div class="container">
      <h2>Foods List</h2>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import Navbar from "@/components/Navbar.vue";

export default {
  name: "Foods",
  components: {
    Navbar,
  },
};
</script>

<style>
</style>