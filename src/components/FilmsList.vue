<template>
    <div>
        <FilmsCard v-for="(movie, i) in moviesList" :key="i" :cardMovie="movie" />
    </div>
</template>

<script>
import FilmsCard from "./FilmsCard.vue";

export default {
    components: {
    FilmsCard
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