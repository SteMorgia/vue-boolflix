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
        
    </div>
</template>

<script>
    export default {
        name: 'MyBody',
        props: {
            filmList: Array
        }
    }
</script>

<style>

</style>