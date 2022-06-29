<template>
    <div>
        <ul>
            <li>
                Title: {{serie.name}} <br />
                Original title: {{serie.original_name}} <br />
                Language: {{serie.original_language}} <br />
                Vote: {{serie.vote_average}} <br />
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    name: "SerieCard",
    props: {
        serie: {
            type: Object,
            requested: true
        }
    }

}
</script>

<style>

</style>