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
      inputUtente: [
        {
          movie: []
        },
        {
          series: []
        }
      ]
    }
  },
  methods: {
    findMovies(param){
      axios.get('https://api.themoviedb.org/3/search/movie?api_key=376598589f212a721599521e853baab1&language=it-IT&query='+param+'&page=1&include_adult=true')
        .then((response)=>{
          this.inputUtente[0].movie = [] 
          this.inputUtente[0].movie.push(response.data.results) 
        })
        axios.get('https://api.themoviedb.org/3/search/tv?api_key=376598589f212a721599521e853baab1&language=it-IT&query='+param+'&page=1&include_adult=true')
        .then((response)=>{
          this.inputUtente[1].series = [] 
          this.inputUtente[1].series.push(response.data.results) 

        })
      
    },
  }
}
</script>

<style lang="scss">
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  background-color: #141414;
  height: 100vh;
}
</style>
