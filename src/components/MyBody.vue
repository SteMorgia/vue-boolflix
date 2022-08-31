<template>
    <div class="container">
        <ul class="movies">
            <li v-for="(film,index) in filmList" :key="index">
                {{film.title}}
                {{film.original_title}}
                <img :src="setFlag(film.original_language)">
                {{film.vote_average}}
            </li>
        </ul>
        <ul>
            <li v-for="(series,index) in seriesList" :key="index">
                {{series.name}}
                {{series.original_name}}
                <img :src="setFlag(series.original_language)">
                {{series.vote_average}}
            </li>
        </ul>
    </div>
</template>

<script>
    export default {
        name: 'MyBody',
        props: {
            filmList: Array,
            seriesList: Array
        },
        data() {
            return {
                flags: ['en', 'it', 'fr', 'es']
            }
        },
        methods: {
            setFlag(original_language) {
                //console.log(original_language)
                //return require('../assets/imgBandiere/' + original_language +'.jpg');
                if (this.flags.includes(original_language)){
                    return require('../assets/imgBandiere/' + original_language +'.jpg');
                } else {
                    original_language;
                }
            }
        }
    }
</script>

<style>

</style>