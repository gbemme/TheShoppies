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
          <v-dialog
              v-model="dialog"
              max-width="350"
              hide-overlay
          >
            <template v-slot:activator="{ on, attrs }">
            <v-icon   v-bind="attrs"
                      v-on="on" @click="dialog=true">mdi-share-variant </v-icon>
            </template>

            <v-card>
              <v-card-title class="font-weight-bold" style="background-color: #FFFFFF">
                Share Movie Link
                <br>
                <br>
              </v-card-title>
              <v-card-text>Please copy the link to share the link to this movie
                <br>
                <small class="blue--text" v-text="$router.currentRoute.path +' '+movie.Title"></small>
              </v-card-text>

            </v-card>
          </v-dialog>

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
  data(){
    return{
      dialog:false
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
      },
      getLink:()=>(movieName)=>{
        return self.$router.currentRoute.path +''+movieName
      }


  },

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