<template>
    <div>
        <ul>
            <li>
                <img :src="'https://image.tmdb.org/t/p/' + 'w200' + serie.poster_path" alt=""> <br />
                Title: {{serie.name}} <br />
                Original title: {{serie.original_name}} <br />
                Language: {{serie.original_language}} <span class="fi" :class="'fi-' + getLanguage"></span> <br />
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
    },
    computed: {
        getLanguage() {
            const langMap = {
                "en" : "us",
                "ja": "jp"
            };
            if(langMap[this.serie.original_language]) {
                return langMap[this.serie.original_language]
            }
            return this.cardMovie.original_language;
        }
    }

}
</script>

<style>

</style>