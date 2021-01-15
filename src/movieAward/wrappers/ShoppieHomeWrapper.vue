<template>
  <div style="overflow-y: hidden">
    <NotificationModal @remove="display=false" :display="display"></NotificationModal>
    <CarouselComponent :height="height" :items="moviesData"></CarouselComponent>
    <SearchComponent  @check="getMovies"></SearchComponent>
    <div class="d-flex mx-auto justify-space-between"  v-if="show" >
        <div class="div-container">
          <p class="ml-8 justify-center align-center">Movies Search Results</p>
        <MovieCard :nomination-list="nominationList" :counter="counter" @count="onClickButton" :movies="moviesData"></MovieCard>
        </div>
      <div class="div-container">
        <p class="align-center justify-center">Your Nominations</p>
      <NominationCard @removeCard="removeNomination" :nomination-list="nominationList"></NominationCard>
      </div>


  </div>
  </div>

</template>

<script>
import CarouselComponent from "@/movieAward/components/CarouselComponent";
import SearchComponent from "@/movieAward/components/SearchComponent";
import MovieCard from '@/movieAward/components/MovieCard'
import NotificationModal from "@/movieAward/components/NotificationModal";
import NominationCard from "@/movieAward/components/NominationCard";
export default {
name: "ShoppieHomeWrapper",
  components: {NominationCard, NotificationModal, SearchComponent, CarouselComponent,MovieCard},
  data(){
    return{
      counter:0,
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
      nominationList:[],
      height:800,
      show:false,
    }
  },
  methods:{
    getMovies(movieName){
      this.height=500;
      this.show = true
      let key = 'b800764b'
      fetch(`https://www.omdbapi.com/?s=${movieName}&apikey=`+ key)
          .then(res=>res.clone().json())
          .then( json =>{
                this.moviesData = json.Search
          }

          )
          .catch((error)=>{ console.log(error)});
    },
    onClickButton(movie){
      if(this.counter<5){
        this.counter++
        if(!this.nominationList.includes(movie)){
          this.nominationList.push(movie)
        }

      }
      else {
        this.display=true
      }
    },
    removeNomination(movie){
      let movieIndex = this.nominationList.indexOf(movie)
      if(movieIndex >-1 && this.counter>0){
        this.nominationList.splice(movieIndex,1)
        this.counter--
      }
    }
  }
}
</script>

<style scoped>
.div-container{
  font-weight: 600;
  font-size: 16px;
  line-height: 20px;

  color: #000000;
}
.wrapper{
  width: 50%;
  justify-content: space-between;
}
</style>