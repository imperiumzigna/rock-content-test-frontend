<template>
  <aside class="left-sidebar">
    <vs-sidebar
      :reduce="reduce"
      :reduce-not-hover-expand="notExpand"
      parent="body"
      default-index="1"
      color="primary"
      class="sidebarx"
      spacer
      v-model="active"
      :hidden-background="true"
    >
      <div class="header-sidebar" slot="header">
        <vs-avatar size="70px" src="https://randomuser.me/api/portraits/men/10.jpg"/>
      </div>
      <vs-sidebar-group open>
        <vs-sidebar-item index="1" icon="list">Tasks</vs-sidebar-item>
        <vs-sidebar-item index="2" icon="turned_in">Contents</vs-sidebar-item>
        <vs-sidebar-item index="3" icon="settings">Setup</vs-sidebar-item>
      </vs-sidebar-group>
    </vs-sidebar>
  </aside>
</template>

<script>
export default {
  name: "LeftSidebar",
  data: () => ({
    active: true,
    notExpand: false,
    reduce: true
  })
};
</script>

<style scoped>
.header-sidebar {
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  width: 100%;
}
.header-sidebar h4 {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 100%;
}
.header-sidebar h4 > button {
  margin-left: 10px;
}
.footer-sidebar {
  display: flex;
  align-items: center;
  justify-content: space-between;
  width: 100%;
}
.footer-sidebar > button {
  border: 0px solid rgba(0, 0, 0, 0) !important;
  border-left: 1px solid rgba(0, 0, 0, 0.07) !important;
  border-radius: 0px !important;
}
</style>