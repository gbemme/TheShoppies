<template>
<div  class="container" >
<!--  <div class="assigned">-->
  <NotificationModal @remove="display=false" :display="display"></NotificationModal>
  <v-row>
    <v-col>
  <div>
    <v-img :src="getImage(movies)" height="240px"></v-img>
  </div>
  <div class="d-flex justify-space-around mt-5">
    <v-btn depressed color="black" class="white--text" large @click="$emit('count')" :disabled="counter===5">
      Nominate
    </v-btn>
    <p>⭐</p>
    <v-icon>mdi-share-variant </v-icon>

  </div>
    </v-col>
  </v-row>
  </div>
<!--</div>-->
</template>

<script>
import NotificationModal from "@/movieAward/components/NotificationModal";
export default {
name: "MovieCard",
  components: {NotificationModal},
  props:{
    movies:Object
  },
  data(){
    return{
      counter:0,
      exceeded:false,
      display:false

    }
  },
    computed:{
      getImage:()=>(item)=>{
        if(item.Poster==='N/A'){
          return 'https://images.unsplash.com/photo-1598899134739-24c46f58b8c0?ixlib=rb-1.2.1&ixid=MXwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHw%3D&auto=format&fit=crop&w=738&q=80'
        }
        else{
          return item.Poster
        }
      }

  },
  methods:{
    onClickButton(){
      if(this.counter<5){
        this.counter++
        this.display=true
      }
      else {
        this.exceeded=true
      }
    }
  }
}
</script>

<style scoped>
.container{
  background: #F9F5FC;
  transform: rotate(0.1deg);
  width: 250px;
  height: 346.31px;
  margin-top: 15px;
}


</style>