<template>
    <div>
        <div class="cover-component" @mouseover="active = true" @mouseleave="active = false">
            <img :src="posterPath"> <br />
            <HoverOnSeries v-if="active" class="serie-information" :serie="serie"/>
        </div>
    </div>
</template>

<script>
import HoverOnSeries from './HoverOnSeries.vue';

export default {
    components: { HoverOnSeries },
    name: "SerieCard",
    props: {
        serie: {
            type: Object,
            requested: true
        }
    },
    data(){
        return {
            active: false,
        }
    },
    computed: {
        posterPath() {
            let url = 'https://image.tmdb.org/t/p/';
            let imgSize = 'w300';
            let poster_path = this.serie.poster_path;
            let replaced_path = '/imgError.png';

            if (poster_path === null) {
                return replaced_path;
            } else {
                return url + imgSize + poster_path;
            }
        },
    }
};
</script>

<style lang="scss">
.cover-component {
    position: relative;
    border: 2px solid black;
    width: 300px;
    height: 450px;

    img {
        width: 100%;
        height: 100%;
    }

    .serie-information {
        position: absolute;
        top: 0;
        left: 0;
        height: 100%;
        width: 100%;
        backdrop-filter: blur(10px);
        background-color: rgba(0, 0, 0, 0.314);
    }
}
</style>