<template>
    <div>
        <Header @search="onSearch" />
        <div class="custom-width">
            <FilmsList class="film-style" :moviesList="moviesList" />
        </div>
        <SeriesList :seriesList="seriesList" />
    </div>

</template>

<script>
import Header from "./TheHeader.vue";
import FilmsList from "./FilmsList.vue";
import SeriesList from "./SeriesList.vue";
import axios from "axios";

export default {
    components: {
        Header, FilmsList, SeriesList
    },
    data() {
        return {
            searchText: "",
            moviesList: [],
            seriesList: [],
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

            axios
                .get('https://api.themoviedb.org/3/search/tv',
                    {
                        params: {
                            api_key: 'a7eb26f7fc5bb3a9457748bc3071c557',
                            query: this.searchText,
                            language: 'it-IT'
                        }
                    })
                .then((resp) => {
                    this.seriesList = resp.data.results;
                })
                .catch(error => {
                    console.log(error);
                });
        },
    },
}
</script>

<style>
.custom-width {
    width: 100%;
}
.film-style{
    flex-grow: 1;
    display: flex;
    justify-content: space-evenly;
    overflow: auto;
    padding: 1.5em;
    gap: 1em;
}
</style>