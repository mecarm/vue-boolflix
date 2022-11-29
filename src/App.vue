<template>
  <div id="app">

    <HeaderComp @emitSearch='findMovies'/>
  </div>
</template>

<script>
import axios from 'axios'
import HeaderComp from './components/HeaderComp.vue'


export default {
  name: 'App',
  components: {
    HeaderComp
  },
  data(){
    return{

    }
  },
  methods: {
    findMovies(param){
      axios.get('https://api.themoviedb.org/3/search/movie?api_key=376598589f212a721599521e853baab1&language=it-IT&query='+param+'&page=1&include_adult=true')
        .then((response)=>{
          console.log(response.data)
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
