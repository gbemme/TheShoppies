<template>
  <div class="overflow-hidden">
    <v-app-bar
        absolute
        color="white"
        elevate-on-scroll
        height="90px"
    >

      <p class="app-title">Shoppie</p>
<!--    <div style="width: 324px">-->
<!--      <v-text-field-->
<!--          label="Search"-->
<!--          light-->
<!--          solo-->
<!--          color="white"-->
<!--          height="40"-->
<!--          prepend-inner-icon="mdi-magnify"-->
<!--          class="mt-7 ml-11 search-no-border"-->
<!--      ></v-text-field>-->
<!--    </div>-->

      <v-spacer/>

    <div class="action-nav">
      <h3>Movie Nominations</h3>

<!--      <v-btn outlined color="rgba(152, 145, 145, 0.97)">-->
<!--        Login-->
<!--      </v-btn>-->

<!--      <v-btn depressed color="#333333" class="white&#45;&#45;text">-->
<!--        Sing up-->
<!--      </v-btn>-->
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