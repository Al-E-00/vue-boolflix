<template>
    <div>
        <Card v-for="(card, i) in moviesList" :key="i" :cardMovies="card"/>
        <Card v-for="(card, i) in seriesList" :key="i" :cardSeries="card" />
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
            required: true
        },
        moviesList: {
            type: Array,
            required: true
        },
    }
}
</script>

<style>

</style>