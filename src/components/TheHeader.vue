<template>
    <div>
        <div class="input-group mb-3">
            <input type="text" class="form-control" placeholder="Search movie" aria-label="Movie's name"
                aria-describedby="button-addon2" v-model="inputSearch">
            <button class="btn btn-outline-secondary" type="button" id="button-addon2" @click="atSearchClick()">Search</button>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
        }
    },
    methods: {
        atSearchClick() {
            this.$emit("search", this.inputSearch);
        }

    }
}
</script>

<style>
</style>