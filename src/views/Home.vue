<template>
  <div class="home">
    <!-- Add row with 12 col -->
    <h3>Setup</h3>
    <vs-tabs>
      <vs-tab vs-label="Home">
        <div>
         
        </div>
      </vs-tab>
      <vs-tab vs-label="Service">
        <div class>Tab</div>
      </vs-tab>
      <vs-tab vs-label="login">
        <div class>Tab</div>
      </vs-tab>
    </vs-tabs>
  </div>
</template>

<script>
// @ is an alias to /src
// import NavBar from "@/components/NavBar.vue";

export default {
  name: "home",
  components: {},
  data() {
    return {
      search: ""
    };
  },
  methods: {
    searchTeam() {
      console.log(this.search);
    }
  }
};
</script>


<style>
.home {
  width: 100%;
}
</style>