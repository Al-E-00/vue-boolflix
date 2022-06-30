<template>
    <div>
        <ul>
            <li>
                <img :src="posterPath"> <br />
                Title: {{serie.name}} <br />
                Original title: {{serie.original_name}} <br />
                Language: {{serie.original_language}} <span class="fi" :class="'fi-' + getLanguage"></span> <br />
                Vote: <MovieRating :vote="serie.vote_average"></MovieRating><br />
            </li>
        </ul>
    </div>
</template>

<script>
import MovieRating from './MovieRating.vue';
export default {
    components: { MovieRating },
    name: "SerieCard",
    props: {
        serie: {
            type: Object,
            requested: true
        }
    },
    computed: {
        getLanguage() {
            const langMap = {
                "en": "us",
                "ja": "jp"
            };
            if (langMap[this.serie.original_language]) {
                return langMap[this.serie.original_language];
            }
            return this.cardMovie.original_language;
        },
        posterPath() {
            let url = 'https://image.tmdb.org/t/p/';
            let imgSize = 'w200';
            let poster_path = this.serie.poster_path;
            let replaced_path = '../public/imgError.png';

            if (poster_path === null) {
                return replaced_path;
            } else {
                return url + imgSize + poster_path;
            }
    },
}
};
</script>

<style>

</style>