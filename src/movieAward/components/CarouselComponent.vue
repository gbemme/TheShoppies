<template>
<div>
  <v-carousel hide-delimiters :height="height" interval="60">
    <v-carousel-item
        v-for="(item,i) in items"
        :key="i"
        :src="getImage(item)"
    >
        <v-row class="fill-height flex-column " style="margin-top: 10%" align="center" justify="center" >
          <p v-text="item.Title" class="display-2 font-weight-bold white--text"></p>
          <br>
          <div class="d-flex justify-lg-space-between" >
            <p style="margin-top: 10px" v-text="item.Year"></p>
          </div>
        </v-row>
    </v-carousel-item>
  </v-carousel>
</div>
</template>

<script>
export default {
name: "CarouselComponent",
  props:{
    items:Array,
    height:[Number,String]
  },
  computed:{
    getImage:()=>(item)=>{
      if(item.Poster==='N/A'){
        return 'https://images.unsplash.com/photo-1598899134739-24c46f58b8c0?ixlib=rb-1.2.1&ixid=MXwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHw%3D&auto=format&fit=crop&w=738&q=80'
      }
      else{
        return item.Poster
      }
    },

  }
}
</script>

<style scoped>

.nominate-btn{
  color: rgba(152, 145, 145, 0.97) !important;
  border-radius: 8px;
  margin-left: 30px !important;
;
}


</style>