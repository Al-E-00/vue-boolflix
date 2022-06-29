<template>
  <div>
    <Header @search="onSearch" />
    <Main :moviesList="moviesList" />
  </div>
</template>

<script>
import Header from "./components/TheHeader.vue";
import Main from "./components/TheMain.vue";
import axios from "axios";


export default {
  components: {
    Header, Main
  },
  data() {
    return {
      searchText: "",
      moviesList: []
    }
  },
  methods: {
    onSearch(searchedItem) {
      this.searchText = searchedItem;

      axios
        .get('https://api.themoviedb.org/3/search/movie',
          {
            params: {
              api_key: 'a7eb26f7fc5bb3a9457748bc3071c557',
              query: this.searchText,
              language: 'it-IT'
            }
          })
        .then((resp) => {
          this.moviesList = resp.data.results;
        })
        .catch(error => {
          console.log(error);
        });
    },
  }
}
</script>

<style  lang="scss">
@import "./assets/scss/main";

</style>