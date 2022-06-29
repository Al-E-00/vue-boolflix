<template>
    <div>
        <ul>
            <li v-for="(movie, i) in cardMovies" :key="i">
                Title: {{ movie.title }} <br />
                Original title:  {{ movie.original_title }} <br /> 
                Language: {{ movie.original_language }} <span class="fi" :class='"fi-" + countryFlag'></span> <br /> 
                Vote: {{ movie.vote_average }} <br />
                
            </li>
        </ul>

    </div>
</template>

<script>

export default {
    name: "MovieCard",
    props: {
        cardMovies: {
            type: Array,
            required: true,
        },
    },
    computed: {
        countryFlag() {
            return this.cardMovies.original_language
        }
    }

}
</script>

<style>

</style>