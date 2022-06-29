<template>
    <div>
        <TvCard v-for="(serie, i) in seriesList" :key="i" :serie="serie"/>
    </div>
</template>

<script>
import TvCard from "./TvSerieCard.vue"

export default {
    name: "seriesList",
    props: {
        seriesList: {
            type: Array, 
            required: true
        }
    },
    components: {
        TvCard
    }

}
</script>

<style>

</style>