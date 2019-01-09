<template>
  <div class="home">
    <!-- Add row with 12 col -->
    <h3>Setup</h3>
    <vs-tabs>
      <vs-tab vs-label="Minha Equipe">
        <div>
          <vs-row vs-type="flex" vs-justify="flex-start">
        <vs-col vs-type="flex" vs-justify="center" vs-align="center" vs-w="4">
          <el-input placeholder="Digite uma palavra-chave e tecle enter para buscar." clearable prefix-icon="el-icon-search" v-model="search"></el-input>  
        </vs-col>
        <vs-col vs-type="flex" vs-justify="flex-end" vs-align="center" vs-w="4">
        <label> Visualizar: </label>

        </vs-col>
        </vs-row>  
        
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
      search: "",
    };
  },
  watch: {
    search: function (value) {
        console.log(value);
      }
  }
};
</script>


<style>
.home {
  width: 100%;
}
</style>