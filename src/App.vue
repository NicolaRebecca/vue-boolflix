<template>
  <div id="app">
    <Header @search="searchMovies" />
    <Main :cards="cards" :tvshow="tvshow" />
  </div>
</template>


<script>
import Header from "./components/Header.vue";
import axios from "axios";
import Main from "./components/Main.vue";
import Tv from "./components/Tv.vue";



export default {
  name: 'App',
  components: {
    Header,
    Main,
    Tv,
    
  },
  data(){
    return {
      filteredMovies: [],
      cards: [],
      tvshow:[]
    }
  },
  created() {
    axios.get("https://api.themoviedb.org/3/movie/popular?api_key=7d3154d492e3c72fd9ee0846bf2ce25c").then((results) => {
      this.cards = results.data.results;
      this.filteredMovies = results.data.results;
    })
    axios.get("https://api.themoviedb.org/3/tv/popular?api_key=7d3154d492e3c72fd9ee0846bf2ce25c&language=en-US&page=1").then((results) => {
      this.tvshow = results.data.results;
      this.filteredMovies = results.data.results;
    })
  },
  methods: {
    searchMovies (searchString){
      if (searchString.lenght == 0){
        this.filteredMovies = this.cards 
        this.filteredMovies = this.tvshow;
        
        return;
      }
      axios.get(`https://api.themoviedb.org/3/search/movie?api_key=7d3154d492e3c72fd9ee0846bf2ce25c&query=${searchString}`).then((results) => {
      this.cards = results.data.results;
      })
      axios.get(`https://api.themoviedb.org/3/search/tv?api_key=7d3154d492e3c72fd9ee0846bf2ce25c&query=${searchString}`).then((results) => {
      this.tvshow = results.data.results;
      })
    }
  },
}

</script>



<style lang="scss">

</style>
