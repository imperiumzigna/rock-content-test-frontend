<template>
  <div class="user-card">
    <el-card :body-style="{ padding: '0px', height: '220px', width: '300px' }">
      <vs-avatar size="90px" :src="user.image_url"/>
      <div style="padding: 14px;">
        <h3>{{user.name}}</h3>
        <h5>{{user.email}}</h5>
      </div>
      <div class="bottom clearfix">
        <el-button
          type="primary"
          @click="$emit('edit_user', user.id)"
          :value="user.id"
          icon="el-icon-edit"
          circle
        ></el-button>
      </div>
    </el-card>
  </div>
</template>

<script>
export default {
  name: "UserCard",
  props: {
    user: Object
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.user-card {
  flex: 1 0 200px;
  box-sizing: border-box;
  padding: 10px;
  margin-left: 10px;
  margin-top: 10px;
}

.clearfix:before,
.clearfix:after {
  display: table;
  content: "";
}

.clearfix:after {
  clear: both;
}

.button {
  padding: 0;
  float: right;
}
</style>
