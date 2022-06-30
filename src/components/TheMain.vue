<template>
    <div class="main-background" :class="click ? 'view-100':'vh-100'">
        <Header @search="onSearch" />
        <div class="slider">
            <FilmsList class="horizontal-scroll-style" :moviesList="moviesList" />
        </div>
        <div class="slider">
            <SeriesList class="horizontal-scroll-style" :seriesList="seriesList" />
        </div>
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
            click: false,
        }
    },
    methods: {
        onSearch(searchedItem) {
            this.searchText = searchedItem;
            this.click = true;

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
</script >

<style>
.view-100{
    height: 100%;
}
.main-background {
    background-color: rgb(20, 20, 20);


}
.slider {
    max-width: 100%;
    display: flex;
}

.horizontal-scroll-style {
    flex-shrink: 0;
    flex-grow: 1;
    display: flex;
    justify-content: space-evenly;
    overflow: auto;
    padding: 1.5em;
    gap: 1em;
    max-width: 100%;
}
</style>