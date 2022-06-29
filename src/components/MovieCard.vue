<template>
    <div>
        <ul>
            <li>
                Title: {{ cardMovies.title }} <br />
                Original title:  {{ cardMovies.original_title }} <br /> 
                Language: {{ cardMovies.original_language }} <br /> 
                Vote: {{ cardMovies.vote_average }} <br />
            </li>
        </ul>
    </div>
</template>

<script>

export default {
    name: "MovieCard",
    props: {
        cardMovies: {
            type: Object,
            required: true,
        },
    },

}
</script>

<style>

</style>