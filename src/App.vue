<template>
  <div id="app">
    <MyHeader  @effettuaRicerca="searching"/>
    <MyBody :filmList='filmList'/>
  </div>
</template>

<script>
import MyBody from './components/MyBody.vue';
import MyHeader from './components/MyHeader.vue';
import axios from 'axios';


export default {
  name: 'App',
  components: {
    MyBody,
    MyHeader
  },
  data() {
    return{
      ApiUrl:'https://api.themoviedb.org/3',
      ApiKey:'0c1bed2d4f67720891185b140a002f33',
      ApiLang:'it-IT',
      filmList:[]
    }
  },
  methods: {
    searching(searchingText) {
      axios.get(this.ApiUrl + '/search/movie?api_key=' + this.ApiKey + '&language=' + this.ApiLang + '&query=' + searchingText)
      .then(response => {
        this.filmList = response.data.results
      }) 
    }
  }
}
</script>

<style lang="scss">

</style>
