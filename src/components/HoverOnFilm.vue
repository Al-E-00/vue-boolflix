<template>
    <div>
        <div class="text-style">
            <p>
                <span class="bold-text">Title: </span> {{ cardMovie.title }} 
            </p>
            <p>
                <span class="bold-text"> Original title:  </span> {{ cardMovie.original_title }}
            </p>
            <p>
                <span class="bold-text"> Language: </span> {{ cardMovie.original_language }} <span class="fi" :class="'fi-' + getLanguage" />
            </p>
            <p>
                <span class="bold-text d-flex gap-2"> Vote: <MovieRating :vote="cardMovie.vote_average"></MovieRating></span> 
            </p>
        </div>
    </div>
</template>

<script>
    import MovieRating from './MovieRating.vue';

export default {
    name: "HoverOnFilm",
    components: { MovieRating },
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
        }
    }

}
</script>

<style lang="scss">
.bold-text {
    font-weight: 500;
}
.text-style{
    color: white;
}

</style>