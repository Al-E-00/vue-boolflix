<template>
    <div>
        <MovieCard :cardMovies="moviesList"/>
    </div>
</template>

<script>
import MovieCard from "./MovieCard.vue";

export default {
    components: {
        MovieCard
    },
    props: {
        moviesList: {
            type: Array,
            required: true,
        },
    }
}
</script>

<style>

</style>