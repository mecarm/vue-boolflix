<template>
  <main class="row overflow-auto p-5">
    <MoviesList  v-for="(element, index) in moviesUtente" :key="index" :detailsMovie="element"/>
  </main>
</template>

<script>
import MoviesList from './MoviesList.vue'

export default {
    name: 'MainComp',
    components: {
        MoviesList
    },
    props: {
        moviesUtente: Object
    }
}
</script>

<style lang="scss" scoped>
    main{
        height: 93%;
    }
</style>