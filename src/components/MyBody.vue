<template>
    <div class="container">
        <ul class="movies">
            <li v-for="(film,index) in filmList" :key="index">
                <img :src="'https://image.tmdb.org/t/p/w300' + film.poster_path" alt="">
                {{film.title}}
                {{film.original_title}}
                <img :src="setFlag(film.original_language)">
                <div>
                    <i v-for="n in 5" class="fa-star" :class="(n > getVote(film.vote_average)) ? 'fa-regular':'fa-solid'" :key="n"></i>
                </div>
            </li>
        </ul>
        <ul>
            <li v-for="(series,index) in seriesList" :key="index">
                <img :src="'https://image.tmdb.org/t/p/w300' + series.poster_path" alt="">
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
            },
            getVote(decimalVote) {
                return Math.ceil(decimalVote / 2);
            }
        }                   
    }
</script>

<style>

</style>