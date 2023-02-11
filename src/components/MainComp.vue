<template>
  <main class="row overflow-auto p-5">
    <!-- Importo componente movies con ciclo -->
    <MoviesList  v-for="(element, index) in moviesUtente[0].movie[0]" :key="index" :detailsMovie="element"/>
    <!-- Importo componente series con ciclo -->
    <SeriesList  v-for="(element, index) in moviesUtente[1].series[0]" :key="index" :detailsSeries="element"/>
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
        moviesUtente: Array
    }
}
</script>

<style lang="scss" scoped>
main {
    height: 90%;
}

main::-webkit-scrollbar-track {
    border: 1px solid #000;
    padding: 2px 0;
    background-color: #404040;
}

main::-webkit-scrollbar {
    width: 10px;
}

main::-webkit-scrollbar-thumb {
    border-radius: 10px;
    box-shadow: inset 0 0 6px rgba(0, 0, 0, .3);
    background-color: #737272;
    border: 1px solid #000;
}
</style>