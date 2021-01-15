<template>
  <div style="width: 40%;margin-top: -40px; margin-left: 31%" class="justify-center align-center d-flex">
    <v-text-field
        label="Search"
        solo
        :light="true"
        height="70"
        v-model="movieName"
        class=".search-border"
        @input="$emit('check',movieName)"
        prepend-inner-icon="mdi-magnify"
    ></v-text-field>
  </div>
</template>

<script>
export default {
name: "SearchComponent",

  data(){
  return{movieName:''}
  },


}
</script>

<style scoped>

</style>