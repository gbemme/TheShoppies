<template>
  <div>
    <CarouselComponent :height="height" :items="moviesData"></CarouselComponent>
    <SearchComponent  @check="getMovies"></SearchComponent>
    <div class="assigned ">
    <v-row v-if="show" class="mx-auto" align-content="center" justify="center"  style="position: absolute;" >
      <v-col v-for="(movie,i) in moviesData" :key="i">
        <MovieCard @count="onClickButton" :movies="movie"></MovieCard>
      </v-col>

    </v-row>
    </div>
  </div>

</template>

<script>
import CarouselComponent from "@/movieAward/components/CarouselComponent";
import SearchComponent from "@/movieAward/components/SearchComponent";
import MovieCard from '@/movieAward/components/MovieCard'
export default {
name: "ShoppieHomeWrapper",
  components: {SearchComponent, CarouselComponent,MovieCard},
  data(){
    return{
      counter:0,
      exceeded:false,
      display:false,

      moviesData:[
        {
          Poster: 'https://m.media-amazon.com/images/M/MV5BOTAzODEzNDAzMl5BMl5BanBnXkFtZTgwMDU1MTgzNzE@._V1_SX300.jpg',
          Title:'Star Wars'
        },
        {
          Poster: 'https://m.media-amazon.com/images/M/MV5BNDc2NTE0NzE4N15BMl5BanBnXkFtZTgwMDQ5MzgwMzE@._V1_SX300.jpg',
          Title:'Silicon Valley'
        },
      ],
      height:800,
      show:false,
    }
  },
  methods:{
    getMovies(movieName){
      this.height=500;
      this.show = true
      let key = 'b800764b'
      console.log('hi')
      console.log(movieName)
      fetch(`https://www.omdbapi.com/?s=${movieName}&apikey=`+ key)
          .then(res=>res.clone().json())
          .then( json =>{
                console.log(json)
                this.moviesData = json.Search
          }

          )
          .catch((error)=>{ console.log(error)});
    },
    onClickButton(){
      if(this.counter<5){
        this.counter++
        this.display=true
        alert(this.counter)
      }
      else {
        this.exceeded=true
        alert(this.counter)
      }
    }
  }
}
</script>

<style scoped>
.assigned {
  /*min-width: 10px;*/
  /*display: flex;*/
  overflow-x: auto;
  max-width: 10% !important;
}
/*.assigned::-webkit-scrollbar {*/
/*  background: transparent !important;*/
/*  width: 2px;*/
/*  max-height: 3px !important;*/
/*}*/
/*.assigned::-webkit-scrollbar-thumb {*/
/*  background: rgba(43, 28, 28, 0.5);*/
/*  max-height: 5px !important;*/
/*  max-width: 20px !important;*/
/*  border-radius: 6px;*/
/*}*/

</style>