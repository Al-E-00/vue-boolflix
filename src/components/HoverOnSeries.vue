<template>
    <div>
        <div class="text-style">
            <p>
                <span class="bold-text">Title: </span> {{ serie.name }}
            </p>
            <p>
                <span class="bold-text"> Original title: </span> {{ serie.original_name }}
            </p>
            <p>
                <span class="bold-text"> Language: </span> {{ serie.original_language }} <span class="fi"
                    :class="'fi-' + getLanguage" />
            </p>
            <p>
                <span class="bold-text d-flex gap-2"> Vote: <MovieRating :vote="serie.vote_average"></MovieRating>
                </span>
            </p>

        </div>
    </div>
</template>

<script>
import MovieRating from './MovieRating.vue';

export default {
    name: "HoverOnSeries",
    components: {
        MovieRating
    },
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

    }
}
</script>

<style>
.bold-text {
    font-weight: 500;
}
.text-style {
    color: white;
}
</style>