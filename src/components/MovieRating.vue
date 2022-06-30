<template>
    <div>
        <span v-for="i in 5" :key="i">
            <i v-if="i <= voteConverted" class="fa-solid fa-star text-warning"></i>
            <i v-else class="fa-regular fa-star"></i>
        </span>
    </div>
</template>

<script>
export default {
    /* 
    vote from 1 to 10 -> vote_average
    */
    props: {
        vote: Number
    },
    computed: {
        voteConverted() {
            return Math.ceil(this.vote / 2);
        }
    }
    }
</script>

<style>
</style>