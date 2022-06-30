<template>
    <div>
        <ul>
            <li>
                <img :src="posterPath" alt=""> <br />
                Title: {{ cardMovie.title }} <br />
                Original title: {{ cardMovie.original_title }} <br />
                Language: {{ cardMovie.original_language }} <span class="fi" :class="'fi-' + getLanguage" />
                <br />
                Vote: <MovieRating :vote="cardMovie.vote_average"></MovieRating> <br />
            </li>
        </ul>
    </div>
</template>

<script>
import MovieRating from './MovieRating.vue';

export default {
    components: { MovieRating },
    name: "MovieCard",
    props: {
        cardMovie: {
            type: Object,
        },
    },
    computed: {
        getLanguage() {
            const langsMap = {
                "en": "us",
                "ja": "jp"
            };
            if (langsMap[this.cardMovie.original_language]) {
                return langsMap[this.cardMovie.original_language];
            }
            return this.cardMovie.original_language;
        },
        posterPath() {
            let url = 'https://image.tmdb.org/t/p/';
            let imgSize = 'w200';
            let poster_path = this.cardMovie.poster_path;
            let replaced_path = '/imgError.png';

            if (poster_path === null) {
                return replaced_path;
            } else {
                return url + imgSize + poster_path;
            }

        },
    },
};
</script>

<style>
</style>