<template>
<div>
   <div  v-for="(movie,i) in NominationList" :key="i" class="container title font-weight-bold  mt-5" >
     <v-card>
       <v-card-title>
         Movie Name : {{movie}}
       </v-card-title>
       <v-card-actions>
         <v-btn @click="$emit('removeCard',movie)" depressed color="red" class="white--text" large>
           Remove
         </v-btn>
       </v-card-actions>
     </v-card>
   </div>
  </div>
</template>

<script>
export default {
name: "NominationCard",
  props:{
    movies:Array,
    display:Boolean,
    counter:Number,
    NominationList:Array
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

}
</script>

<style scoped>
.container{
  background: #F9F5FC;
  transform: rotate(0.1deg);
  width: 350px;
}
.title{
  font-size: 20px;
}


</style>