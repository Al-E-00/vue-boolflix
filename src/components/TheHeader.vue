<template>
    <div>
        <div class="d-flex header-style">
            <img src="../assets/img/logo.png" alt="">
            <div class="input-group input-style">
                <input type="text" class="form-control" placeholder="Search movie and tv series" aria-label="Movie's name"
                    aria-describedby="button-addon2" v-model="inputSearch" @keyup.enter="atSearchClick()">
                <button class="btn btn-secondary" type="button" id="button-addon2" @click="atSearchClick()">Search</button>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            inputSearch: "",
        }
    },
    methods: {
        atSearchClick() {
            this.$emit("search", this.inputSearch);
            this.inputSearch = "";
        }

    }
}
</script>

<style lang="scss" scoped>
    .header-style {
        background-color: black;
        img {
            width: 200px;
            padding: .4rem;
        }
    .input-style {
        width: 300px;
        height: 40px;
        align-self: center;
        margin-left: 52em;
    }
    }
</style>