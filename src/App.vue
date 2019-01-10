<template>
  <div id="app">
    <left-sidebar/>
    <vs-row>
      <vs-col vs-offset="1" vs-type="flex" vs-justify="left" vs-align="left" vs-w="11">
        <router-view/>
      </vs-col>
    </vs-row>
  </div>
</template>

<script>
import LeftSidebar from "./components/LeftSidebar.vue";

export default {
  name: "app",
  components: {
    LeftSidebar
  }
};
</script>

<style>
body {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  background-color: #e4e8ec;
  margin-top: 60px;
}
</style>
