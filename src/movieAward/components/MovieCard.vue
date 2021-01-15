<template>
<div>
  <v-row class="row-container">
    <v-col  class="container"  v-for="(movie,i) in movies" :key="i">
        <div>
          <v-img :src="getImage(movie)" height="200px"></v-img>
        </div>
         <div class="d-flex title font-weight-bold justify-space-around mt-5" >
           <p v-text="movie.Title"></p>
           <p v-text="movie.Year"></p>
         </div>
        <div class="d-flex justify-space-around mt-3">
          <v-btn depressed color="black" class="white--text" large id="nominate" @click="$emit('count',movie.Title)" :disabled="NominationList.includes(movie.Title)">
            Nominate
          </v-btn>
      <!--    <p class="mt-4">⭐<span>movies.imdbRating</span></p>-->
          <v-icon>mdi-share-variant </v-icon>

        </div>
    </v-col>
  </v-row>
  </div>
<!--</div>-->
</template>

<script>
export default {
name: "MovieCard",
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
  width: 230px;
  /*height: 3.31px;*/
  /*margin-top: 15px;*/
  margin: 20px;
}
.title{
  font-size: 20px;
}
.row-container{
  min-width: 65%;
  width: 70%;
}


</style>