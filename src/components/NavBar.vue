<template>
  <div class="navbar">
    <vs-navbar :type="flat" v-model="activeItem" class="nabarx">
      <vs-spacer></vs-spacer>
      <vs-navbar-item index="0">Setup</vs-navbar-item>
    </vs-navbar>
  </div>
</template>

<script>
export default {
  name: "Navbar",
  data: () => ({
    activeItem: 0
  })
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
