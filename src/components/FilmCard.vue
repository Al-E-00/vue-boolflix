<template>
    <div>
        <ul>
            <li>
                Title: {{ cardMovie.title }} <br />
                Original title: {{ cardMovie.original_title }} <br />
                Language: {{ cardMovie.original_language }} <span class="fi" :class="'fi-' + getLanguage" />
                <br />
                Vote: {{ cardMovie.vote_average }} <br />
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
    },

};
</script>

<style>
</style>