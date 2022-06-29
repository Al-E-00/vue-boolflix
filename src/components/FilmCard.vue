<template>
    <div>
        <ul>
            <li>
                <img :src="'https://image.tmdb.org/t/p/' + 'w200' + cardMovie.poster_path" alt=""> <br />
                Title: {{ cardMovie.title }} <br />
                Original title: {{ cardMovie.original_title }} <br />
                Language: {{ cardMovie.original_language }} <span class="fi" :class="'fi-' + getLanguage" />
                <br />
                Vote: {{ voteConverted }} <br />
            </li>
        </ul>
    </div>
</template>

<script>

export default {
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
                return langsMap[this.cardMovie.original_language]
            }
            return this.cardMovie.original_language;
        },
        voteConverted() {
            let number = this.cardMovie.vote_average / 2;
            let convertedNumber = parseInt(number);
            return convertedNumber;
        }
    },

};
</script>

<style>
</style>