<template>
    <div>
        <div class="cover-component" @mouseover="active = true" @mouseleave="active = false">
            <img :src="posterPath" alt="">
            <HoverOnFilm v-if="active" class="movie-information" :cardMovie="cardMovie"></HoverOnFilm>
        </div>
    </div>
</template>

<script>
import HoverOnFilm from './HoverOnFilm.vue';

export default {
    components: { HoverOnFilm },
    name: "MovieCard",
    props: {
        cardMovie: {
            type: Object,
        },
    },
    data() {
        return {
            active: false,
        }
    },
    computed: {
        posterPath() {
            let url = 'https://image.tmdb.org/t/p/';
            let imgSize = 'w300';
            let poster_path = this.cardMovie.poster_path;
            let replaced_path = '/imgError.png';

            if (poster_path === null) {
                return replaced_path;
            } else {
                return url + imgSize + poster_path;
            }
        },

    },
};
</script>

<style lang="scss">
.cover-component {
    position: relative;
    border: 2px solid black;
    width: 300px;
    height: 450px;


    img{
        width: 100%;
        height: 100%;
    }
    
    .movie-information {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        backdrop-filter: blur(10px);
        background-color: rgba(0, 0, 0, 0.314);

    }
}
</style>