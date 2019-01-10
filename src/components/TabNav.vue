<template>
  <div class="tabnav">
    <vs-row vs-type="flex" vs-justify="space-between" vs-w="12">
      <vs-col vs-type="flex" vs-justify="flex-start" vs-align="center" vs-w="1">
        <h3>Setup</h3>
      </vs-col>
      <vs-col vs-type="flex" vs-justify="space-around" vs-align="center" vs-w="2">
        <vs-dropdown>
          <a class="a-icon" href.prevent>
            Olá
            <i class="material-icons">expand_more</i>
          </a>
          <vs-dropdown-menu>
            <vs-dropdown-item>Option 1</vs-dropdown-item>
            <vs-dropdown-item>Option 2</vs-dropdown-item>
            <vs-dropdown-item divider>Option 3</vs-dropdown-item>
          </vs-dropdown-menu>
        </vs-dropdown>
      </vs-col>
    </vs-row>
  </div>
</template>

<script>
export default {
  name: "TabNav"
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
