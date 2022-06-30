<template>
    <div class="d-flex">
        <FilmCard v-for="(movie, i) in moviesList" :key="i" :cardMovie="movie" />
    </div>
</template>

<script>
import FilmCard from "./FilmCard.vue";

export default {
    components: {
    FilmCard
    },
    props: {
        moviesList: {
            type: Array,
            required: true
        },
    },
};
</script>

<style>

</style>