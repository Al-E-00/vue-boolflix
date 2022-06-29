<template>
    <div>
        <ul>
            <li>
                Title: {{ cardMovies.title }} <br />
                Original title:  {{ cardMovies.original_title }} <br /> 
                Language: {{ cardMovies.original_language }} <span class="fi" :class="'fi-' + getLanguage" /> <br /> 
                Vote: {{ cardMovies.vote_average }} <br />
            </li>
        </ul>
    </div>
</template>

<script>

export default {
    name: "MovieCard",
    props: {
        cardMovies: {
            type: Object,
            required: true,
        },
    },
    computed: {
        getLanguage() {
            const langsMap = {
                "en" : "us",
                "ja" :"jp"
            };
            if(langsMap[this.cardMovies.original_language]){
                return langsMap[this.cardMovies.original_language]
            }
            return this.cardMovies.original_language;
        },
    },

};
</script>

<style>

</style>