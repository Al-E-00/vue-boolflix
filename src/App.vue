<template>
  <div>
    <Header @search="movieSearch"/>
    <Main />
  </div>
</template>

<script>
import Header from "./components/TheHeader.vue";
import Main from "./components/TheMain.vue";
import Axios from "axios"


export default {
  components: {
    Header, Main
  },
  data() {
    return {
      searchMovie: "",
    }
  },
  methods: {
    fetchMoviesList() {
      Axios.
      get("https://api.themoviedb.org/3/search/movie", {
        params: {
          api_key: "a7eb26f7fc5bb3a9457748bc3071c557",
          query: this.searchMovie,
          language: "it-IT"
        }
      });
      },
      movieSearch(reserch){
        this.searchMovie = reserch;
        console.log(this.searchMovie)
      }
    },
    }
</script>

<style>

</style>