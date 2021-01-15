<template>
  <div class="overflow-hidden">
    <v-app-bar
        fixed
        color="white"
        elevate-on-scroll
        height="80px"
    >
      <p class="app-title">Shoppie</p>
      <v-spacer/>

    <div class="action-nav">
      <h3>Movie Nominations</h3>
    </div>

    </v-app-bar>
  </div>
</template>

<script>
export default {
name: "ShoppiesHeader"
}
</script>

<style scoped>
.app-title{
  font-style: normal;
  font-weight: 800;
  font-size: 30px;
  line-height: 36px;
  color: #000000;
}
.action-nav{
  display: flex;
  /*width: 24%;*/
  /*justify-content: space-between;*/
}


</style>