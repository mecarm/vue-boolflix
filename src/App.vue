<template>
  <div id="app">

    <HeaderComp @emitSearch='findMovies'/>
    <MainComp :moviesUtente='inputUtente'/>
  </div>
</template>

<script>
import axios from 'axios'
import HeaderComp from './components/HeaderComp.vue'
import MainComp from './components/MainComp.vue'


export default {
  name: 'App',
  components: {
    HeaderComp,
    MainComp
  },
  data(){
    return{
      inputUtente: ''
    }
  },
  methods: {
    findMovies(param){
      axios.get('https://api.themoviedb.org/3/search/movie?api_key=376598589f212a721599521e853baab1&language=it-IT&query='+param+'&page=1&include_adult=true')
        .then((response)=>{
          this.inputUtente = response.data.results
        })
    }
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  background-color: #141414;
  height: 100vh;
}
</style>
