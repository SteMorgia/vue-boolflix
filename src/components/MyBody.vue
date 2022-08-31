<template>
    <div class="container">
        <ul class="movies">
            <li v-for="(film,index) in filmList" :key="index">
                {{film.title}}
                {{film.original_title}}
                {{film.original_language}}
                {{film.vote_average}}
            </li>
        </ul>
        <ul>
            <li v-for="(series,index) in seriesList" :key="index">
                {{series.name}}
                {{series.original_name}}
                {{series.original_language}}
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
        }
    }
</script>

<style>

</style>