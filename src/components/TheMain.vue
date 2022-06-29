<template>
    <div>
        <MovieCard v-for="(card, i) in moviesList" :key="i" :cardMovies="card"/>
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