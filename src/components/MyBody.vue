<template>
    <div class="container">
        <section class="movies">
            <div v-for="(film,index) in filmList" :key="index" class="moviesCard">
                <img :src="'https://image.tmdb.org/t/p/w300' + film.poster_path" alt="">

                <div class="info">
                    <p>{{film.title}}</p>
                    <p>{{film.original_title}}</p>
                    <img :src="setFlag(film.original_language)">
                    <div>
                        <i v-for="n in 5" class="fa-star" :class="(n > getVote(film.vote_average)) ? 'fa-regular':'fa-solid'" :key="n"></i>
                    </div>
                </div>
                
            </div>
        </section>
        
        <ul>
            <li v-for="(series,index) in seriesList" :key="index">
                <img :src="'https://image.tmdb.org/t/p/w300' + series.poster_path" alt="">
                {{series.name}}
                {{series.original_name}}
                <img :src="setFlag(series.original_language)">
                <div>
                    <i v-for="n in 5" class="fa-star" :class="(n > getVote(series.vote_average)) ? 'fa-regular':'fa-solid'" :key="n"></i>
                </div>
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

<style scoped lang="scss">
    .container {
        background-color: rgb(88, 88, 88);
        height:100%;

        .movies {
            display:flex;
            flex-wrap:wrap;
            justify-content:space-between;
            align-items:center;
            padding:1rem;
        }
    }
</style>