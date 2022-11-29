<template>
  <main class="row overflow-auto p-5">
    <MoviesList  v-for="(element, index) in moviesUtente[0].movie[0]" :key="index" :detailsMovie="element"/>
    <SeriesList  v-for="(element, index) in moviesUtente[1].series[0]" :key="index" :detailsMovie="element"/>
  </main>
</template>

<script>
import MoviesList from './MoviesList.vue'
import SeriesList from './SeriesList.vue'

export default {
    name: 'MainComp',
    components: {
        MoviesList,
        SeriesList
    },
    props: {
        moviesUtente: Object
    }
}
</script>

<style lang="scss" scoped>
    main{
        height: 90%;
    }
</style>