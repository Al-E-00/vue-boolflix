<template>
    <div>
        <Card v-for="(card, i) in moviesList" :key="'movies' + i" :cardMovies="card"/>
        <Card v-for="(card, i) in seriesList" :key="'series' + i" :cardSeries="card" />
    </div>
</template>

<script>
import Card from "./ResultCard.vue";

export default {
    components: {
        Card
    },
    props: {
        seriesList: {
            type: Array,
        },
        moviesList: {
            type: Array,
        },
    }
}
</script>

<style>

</style>