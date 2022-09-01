<template>
    <div class="container">
        <section class="movies">
            <div v-for="(film,index) in filmList" :key="index" class="moviesCard flip-card">
                <div class="flip-card-inner">
                    <div class="flip-card-front">
                        <img :src="'https://image.tmdb.org/t/p/w300' + film.poster_path">
                    </div>
                    <div class="flip-card-back">
                        <h1>{{film.title}}</h1>
                        <div>
                            <i v-for="n in 5" class="fa-star" :class="(n > getVote(film.vote_average)) ? 'fa-regular':'fa-solid'" :key="n"></i>
                        </div>
                        <img :src="setFlag(film.original_language)">
                        <p>{{film.overview}}</p>
                    </div>
                </div>
            </div>
        </section>

        <section class="series">
            <div v-for="(series,index) in seriesList" :key="index" class="moviesCard flip-card">
                <div class="flip-card-inner">
                    <div class="flip-card-front">
                        <img :src="'https://image.tmdb.org/t/p/w300' + series.poster_path">
                    </div>
                    <div class="flip-card-back">
                        <h1>{{series.name}}</h1>
                        <div>
                            <i v-for="n in 5" class="fa-star" :class="(n > getVote(series.vote_average)) ? 'fa-regular':'fa-solid'" :key="n"></i>
                        </div>
                        <img :src="setFlag(series.original_language)">
                        <p>{{series.overview}}</p>
                    </div>
                </div>
            </div>
        </section>
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
    .movies, .series {
        display:flex;
        justify-content: space-between;
        align-items: center;
        flex-wrap:wrap;
        height:calc(100vh - 100px);
    }
    .flip-card {
        background-color: transparent;
        perspective: 1000px;
        width:25%;
        height:100%;
        padding:1rem;

        .flip-card-front img {
            height:100%;
        }

        .flip-card-inner {
            position: relative;
            width: 100%;
            height: 100%;
            text-align: center;
            transition: transform 0.8s;
            transform-style: preserve-3d;
        }
        .flip-card-front, .flip-card-back {
            position: absolute;
            width: 100%;
            height: 100%;
            -webkit-backface-visibility: hidden; 
            backface-visibility: hidden;
        }
        .flip-card-back {
            background-color: rgb(0, 0, 0);
            color: white;
            transform: rotateY(180deg);
        }
    }
    .flip-card:hover .flip-card-inner {
        transform: rotateY(180deg);
    }
</style>